# Walkthrough

## Target Details
- Download Link: https://www.vulnhub.com/entry/shenron-1,630/
- Name: shenron 1
- Date release: 15 Dec 2020
- Author: [Shubham mandloi](https://www.vulnhub.com/author/shubham-mandloi,768/)
- Series: [shenron](https://www.vulnhub.com/series/shenron,427/)
- Difficulty: Easy
- Tags: Fuzzing, Web CMS, Directory Listing, Stored Credentials, SUIDs
- Avg Completion Time: 1.5 Hours

## Popular Tools
- Feroxbuster
- [Penelope Shell Handler](https://github.com/brightio/penelope)
- [GTFOBins](https://gtfobins.github.io/)

## Hints

>[!hint] Initial Access
>[Hint #1](## "Have you found the Joomla Admin interface?")
>[Hint #2](## "Did you run DirBuster and locate interesting files?")
>[Hint #3](## "Did you explore the Joomla Administrator CMS and exploit Default Configurations?")
>[Hint #4](## "Have you used Default Templates to modify available site details to include a php reverse shell?")
>

>[!hint] Shell Access
>[Hint #1](## "Have you searched for configuration and possible `password` files?")
>[Hint #2](## "Have you elevated yourself from service access to user access?")
>[Hint #3](## "Have you enumerated User Access to escalate to Elevated User Access?")
>[Hint #4](## "Have you used the CP command to escalate to SSH Access?")
>

>[!hint] SSH Access
>[Hint #1](## "Have you found the `password` file?")
>[Hint #2](## "Have you Enumerated the capabilities of the Elevated User?")
>[Hint #3](## "Have you searched GTFObins for the appropriate PrivEsc?")
>

## Enumeration

Start with a simple nmap scan just to get an initial target to manually explore and efficiently utilize the time. `nmap {target}`

![[Nmap Quick Scan]]

Once the initial scan completes, begin by enumerating discovered services and scanning for any port missed in the initial scan. 
- Full port scan: `nmap {shenron_ip} -p-`
- Enumeration and save output: `nmap -p- -sV -sC -oN {path/to/output/file} {target}` 

![[Nmap Full Service Scan]]

The results show that only ports 22 and 80 are `open` and an Apache2 web server showing the default page.

![[Apache2 Web Page.png]]

Executing a Bruteforce Directory enumeration scan using feroxbuster, multiple interesting directories and files are found that require investigation.

- `feroxbuster -u http://{shenron_ip} -w /usr/share/wordlists/dirb/common.txt`
```bash
┌──(cab00s3㉿proxmox-kali-ctf)-[~]
└─$ feroxbuster -u http://{shenron_ip} -w /usr/share/wordlists/dirb/common.txt

 ___  ___  __   __     __      __         __   ___
|__  |__  |__) |__) | /  `    /  \ \_/ | |  \ |__
|    |___ |  \ |  \ | \__,    \__/ / \ | |__/ |___
by Ben "epi" Risher                    ver: 2.10.2
───────────────────────────┬──────────────────────
     Target Url            │ http://{shenron_ip}
     Threads               │ 50
     Wordlist              │ /usr/share/wordlists/dirb/common.txt
     Status Codes          │ All Status Codes!
     Timeout (secs)        │ 7
     User-Agent            │ feroxbuster/2.10.2
     Config File           │ /etc/feroxbuster/ferox-config.toml
     Extract Links         │ true
     HTTP methods          │ [GET]
     Recursion Depth       │ 4
     New Version Available │ https://github.com/epi052/feroxbuster/releases/latest
───────────────────────────┴──────────────────────
   Press [ENTER] to use the Scan Management Menu™
──────────────────────────────────────────────────
...Omitted For Brevity... 
[####################] - 5s      4614/4614    892/s   http://{shenron_ip}/ 
[####################] - 26s     4614/4614    175/s   http://{shenron_ip}/joomla/ 
[####################] - 0s      4614/4614    44796/s http://{shenron_ip}/test/ => Directory listing
```

Inside the `/test` Directory Listing a file is discovered and show some interesting output once viewing the source of the document.

![[Shenron_password_file.png]]

Viewing the source reveals hidden credentials with the file.

![[Shenron_ViewSource_password.png]]

The feroxbuster results also include a `/joomla` path and as expected the `/joomla/administrator` path gives us the Joomla Administration login screen of which the recovered credentials are very useful.
![[Shenron_Joomla_Admin.png]]

## Joomla

Access to the Joomla Content Management System (CMS) allows an authenticated user to modify the contents of the site and in the hands of a malicious user will be utilized to gain increased privileges to the Host system. The next step is to Identify a pathway to exploit the administrative capabilities to gain shell access.

There are a few methods that can be used to modify the current file structure to execute arbitrary code. 
1. Install and use a file manger component to the CMS to modify the contents of the web directory.
	- http://www.mooj.org/en/extensions/components/profiles-joomla-web-file-manager/download-profiles.html
2. Directly modify the existing contents to execute malicious code to have the system execute a reverse shell.
	- Using the Templates component already installed and modify the contents of the templates.
	- Modifying the `index.php` file will overwrite the contents of the homepage of the application.  This is destructive and is not the preferred method.
	- Adding a file to the template that can be accessed directly is the preferred method and is the method used here.
### Protostar Template Modification

The default template for this instance is the Protostar Templates.

![[Shenron_Joomla_Default_Template.png]]

Access the Protostar Template and edit the contents to gain shell access.

![[Shenron_Joomla_Protostar_Template.png]]

Add a file to the template and with the name `shell.php`

![[Shenron_Joomla_Protostar_New_File.png]]

Go to https://revshells.com and select the PHP PentestMonkey reverse shell generator and add to the shell.php file.

![[Shenron_Shell_Generator.png]]

Save and Close the Editor and prepare the listener for the reverse shell.

![[Shenron_Joomla_Protostar_Shell_php.png]]

The `/templates` directory is under the root joomla path and can be accessed directly by browsing to the path for the edited files. Browsing to http://{shenron}/joomla/templates/protostar/shell.php will execute the shell and utilizing [Penelope Shell Handler](https://github.com/brightio/penelope)the shell will escalate to a full PTY shell allowing full capabilities. 

![[Penelope Reverse Shell]]
## Shell Access

Shell access grants the attacker access to the files directly on the target device and with the current user `www-data`. Begin to explore and enumerate the machine: 
- locate users: `cat /etc/passwd`
- search for configuration files
- search for interesting .txt files
- search for `SUID` binaries
- check sudo capabilities

![[Configuration Files]]
![[Stored Credentials]]
Credentials are stored with the configuration file `configuration.php` for `jenny` granting the ability to `su` to a new user and continue to enumerate and explore the system. The new user has an interesting capability to run the `/usr/bin/cp` binary creating a pathway to gain elevated user access.

![[User Enumeration]]

The `cp` command allows the user to copy a file to any location which, in this case, can be used to copy the `authorized_keys` containing the required key to grant ssh access to the system as the `shenron` user.  

![[User Privilege Escalation]]

## SSH access

Now with ssh access to the system, persistent access has been obtained and access to a different user. Logging in as the user `shenron`, the local flag is accessible in `shenron`'s `/home/shenron` directory.

![[SSH Access]]
![[Local Flag]]

Also, remembering the `password.txt` file identified earlier, the contents are now readable and provide the necessary user password for `shenron`. Continue to enumerate the system, using the techniques previously executed.  The `shenron` user also has an interesting capability of using the `/usr/bin/apt` command through sudo privileges.   
![[Root Privilege Escalation]]

Checking [GTFOBins](https://GTFOBins.github.io), under Sudo option (c):
	When the shell exits the `update` command is actually executed.
			```
		sudo apt update -o APT::Update::Pre-Invoke::=/bin/sh
		```
Executing the command as `shenron` and using the password from the `/var/opt/password.txt` a root shell is created and access the `/root` directory containing the `root.txt`

![[Root Flag]]

# Congratulations and Thank You!!!
