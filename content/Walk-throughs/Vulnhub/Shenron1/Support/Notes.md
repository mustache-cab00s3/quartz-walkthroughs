# Notes
## Discovery

^b7d994

### Nmap
- Quick Scan
	- `nmap {shenron_ip}`
	- [[Nmap Quick Scan]]
	- ports 22, 80
- Full Scan
	- `nmap {shenron_ip}  -p-`
	- [[Nmap Full Scan]]
	- protocols ssh, http
## Fuzzing/DirBusting

^98bd4a

### Content Discovery
- Feroxbuster
	- `feroxbuster -u http://{shenron_ip} -w /usr/share/wordlists/dirb/common.txt`
	- [[Feroxbuster]]
	- http://{shenron_ip}/test/ => Directory listing
		- [[Shenron_dir_listing.png]]
		- [[Shenron_password_file.png]]
		- [[Shenron_ViewSource_password.png]]
	- http://{shenron_ip}/joomla/administrator/ 
		- login with collected creds
		- [[Shenron_Joomla_Admin.png]]

## Exploitation

^d03654

### Initial Access
- locate default template applied
	- [[Shenron_Joomla_Templates.png]]
	- [[Shenron_Joomla_Default_Template.png]]
- modify index.php file with additional reverse shell code
	- [[Shenron_Shell_Generator.png]]
- get shell from www-data
	- Use penelope shell handler
		- https://github.com/brightio/penelope
		- `└─$ python3 ~/Github/penelope/penelope.py 1337`
		- browse to http://{shenron_ip}/joomla/ to execute shell code
		- [[#Penelope Reverse Shell]]

### Privilege Escalation

^3a7475

#### User Level
- Shell Access with `www-data` user
	- [[Penelope Reverse Shell]]
- Enumeration at initial shell
	- [[/etc/passwd]]
	- [[Configuration Files]]
	- [[ls /home]]
- User access with password
	- Enumerate user privileges
		- [[User Access]]
		- [[User Enumeration]]
	- [[Stored Credentials]]
#### Elevated Level
- Elevated User Access
	- Use User privileges to access elevated user's directories and gain Elevated User Access
		- [[User Privilege Escalation]]
		- [[SSH Access]]
		- [[Local Flag]]
	- Use Stored credentials to escalate to `root`
		- [[Root Privilege Escalation]]
		- [[Root Flag]]

## Reporting

### Evidence
[[Nmap Quick Scan]]
[[Nmap Full Scan]]

[[Nmap Full Service Scan]]

#### Apache2 Web Page
![[Apache2 Web Page.png]]

[[Feroxbuster]]

#### Web /Test
##### ![[Shenron_dir_listing.png]]
##### ![[Shenron_password_file.png]]
[[Source File]]

##### ![[Shenron_ViewSource_password.png]]
![[Shenron_Joomla_Admin.png]]

![[Shenron_Joomla_Templates.png]]
![[Shenron_Joomla_Default_Template.png]]

![[Shenron_Joomla_Protostar_Template.png]]


![[Shenron_Joomla_Protostar_New_File.png]]

![[Shenron_Joomla_Protostar_Shell_php.png]]

![[Shenron_Shell_Generator.png]]
[[PHP Reverse Shell]]

[[Penelope Reverse Shell]]
#### Shell Enumeration
[[passwd]]
##### ls /home
```bash
www-data@shenron:/$ ls /home
jenny  shenron
```
[[Configuration Files]]

#### User Access
[[User Enumeration]]
[[Stored Credentials]]
[[User Privilege Escalation]]

#### Elevated User Access
[[SSH Access]]
[[Local Flag]]

[[Root Privilege Escalation]]

[[Root Flag]]