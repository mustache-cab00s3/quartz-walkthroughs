
```bash

shenron@shenron:~$ sudo -l
[sudo] password for shenron: 

shenron@shenron:~$ ls -ial /var/opt/password.txt 
393338 -rwx------ 1 shenron shenron 43 Dec 13  2020 /var/opt/password.txt

shenron@shenron:~$ cat /var/opt/password.txt 
shenron : YoUkNowMyPaSsWoRdIsToStRoNgDeAr

shenron@shenron:~$ sudo -l
[sudo] password for shenron: 
Matching Defaults entries for shenron on shenron:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User shenron may run the following commands on shenron:
    (ALL : ALL) /usr/bin/apt
shenron@shenron:~$ 

```