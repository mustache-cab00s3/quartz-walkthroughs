
```bash
┌──(cab00s3㉿proxmox-kali-ctf)-[~]
└─$ nmap -p- -sV -sC -oN shenron.nmap {shenron_ip} 
Starting Nmap 7.94SVN ( https://nmap.org ) at 2024-07-24 14:44 CDT
Nmap scan report for shenron (192.168.1.18)
Host is up (0.0014s latency).
Not shown: 65533 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 8.2p1 Ubuntu 4ubuntu0.1 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   3072 0e:22:60:0a:f7:d4:78:f6:42:08:d7:6a:6b:b0:b1:62 (RSA)
|   256 b3:0c:cd:0a:67:c3:ab:d2:23:27:02:1f:b2:fb:91:12 (ECDSA)
|_  256 29:73:e0:f2:6d:f6:fb:de:4c:6f:b2:7a:19:69:f5:82 (ED25519)
80/tcp open  http    Apache httpd 2.4.41 ((Ubuntu))
|_http-server-header: Apache/2.4.41 (Ubuntu)
|_http-title: Apache2 Debian Default Page: It works
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 11.59 seconds

```