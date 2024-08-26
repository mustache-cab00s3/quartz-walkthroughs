#### Feroxbuster
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
[####################] - 76s     4614/4614    60/s    http://{shenron_ip}/joomla/administrator/ 
[####################] - 23s     4614/4614    198/s   http://{shenron_ip}/joomla/bin/ 
[####################] - 30s     4614/4614    155/s   http://{shenron_ip}/joomla/cache/ 
[####################] - 63s     4614/4614    73/s    http://{shenron_ip}/joomla/components/ 
[####################] - 71s     4614/4614    65/s    http://{shenron_ip}/joomla/includes/ 
[####################] - 60s     4614/4614    77/s    http://{shenron_ip}/joomla/images/ 
[####################] - 68s     4614/4614    68/s    http://{shenron_ip}/joomla/layouts/ 
[####################] - 62s     4614/4614    75/s    http://{shenron_ip}/joomla/libraries/ 
[####################] - 68s     4614/4614    68/s    http://{shenron_ip}/joomla/language/ 
[####################] - 68s     4614/4614    68/s    http://{shenron_ip}/joomla/media/ 
[####################] - 61s     4614/4614    75/s    http://{shenron_ip}/joomla/modules/ 
[####################] - 47s     4614/4614    98/s    http://{shenron_ip}/joomla/plugins/ 
[####################] - 6s      4614/4614    773/s   http://{shenron_ip}/joomla/plugins/authentication/ => Directory listing
[####################] - 7s      4614/4614    616/s   http://{shenron_ip}/joomla/plugins/captcha/ => Directory listing
[####################] - 60s     4614/4614    76/s    http://{shenron_ip}/joomla/tmp/ 
[####################] - 7s      4614/4614    629/s   http://{shenron_ip}/joomla/plugins/content/ => Directory listing
[####################] - 7s      4614/4614    630/s   http://{shenron_ip}/joomla/plugins/editors/ => Directory listing
[####################] - 0s      4614/4614    11038/s http://{shenron_ip}/joomla/plugins/extension/ => Directory listing
[####################] - 9s      4614/4614    531/s   http://{shenron_ip}/joomla/plugins/fields/ => Directory listing
[####################] - 7s      4614/4614    655/s   http://{shenron_ip}/joomla/images/banners/ => Directory listing
[####################] - 7s      4614/4614    641/s   http://{shenron_ip}/joomla/plugins/installer/ => Directory listing
[####################] - 8s      4614/4614    609/s   http://{shenron_ip}/joomla/media/cms/ => Directory listing
[####################] - 7s      4614/4614    654/s   http://{shenron_ip}/joomla/media/contacts/ => Directory listing
[####################] - 7s      4614/4614    643/s   http://{shenron_ip}/joomla/libraries/cms/ => Directory listing
[####################] - 7s      4614/4614    646/s   http://{shenron_ip}/joomla/images/headers/ => Directory listing
[####################] - 45s     4614/4614    104/s   http://{shenron_ip}/joomla/administrator/cache/ 
[####################] - 8s      4614/4614    605/s   http://{shenron_ip}/joomla/plugins/privacy/ => Directory listing
[####################] - 8s      4614/4614    612/s   http://{shenron_ip}/joomla/media/editors/ => Directory listing
[####################] - 8s      4614/4614    565/s   http://{shenron_ip}/joomla/administrator/components/ => Directory listing
[####################] - 8s      4614/4614    596/s   http://{shenron_ip}/joomla/plugins/search/ => Directory listing
[####################] - 7s      4614/4614    658/s   http://{shenron_ip}/joomla/libraries/joomla/ => Directory listing
[####################] - 1s      4614/4614    5255/s  http://{shenron_ip}/joomla/libraries/legacy/ => Directory listing
[####################] - 8s      4614/4614    573/s   http://{shenron_ip}/joomla/plugins/system/ => Directory listing
[####################] - 7s      4614/4614    625/s   http://{shenron_ip}/joomla/layouts/libraries/ => Directory listing
[####################] - 7s      4614/4614    637/s   http://{shenron_ip}/joomla/administrator/help/ => Directory listing
[####################] - 6s      4614/4614    773/s   http://{shenron_ip}/joomla/plugins/user/ => Directory listing
[####################] - 7s      4614/4614    637/s   http://{shenron_ip}/joomla/administrator/includes/ => Directory listing
[####################] - 7s      4614/4614    633/s   http://{shenron_ip}/joomla/media/mailto/ => Directory listing
[####################] - 7s      4614/4614    635/s   http://{shenron_ip}/joomla/media/media/ => Directory listing
[####################] - 7s      4614/4614    632/s   http://{shenron_ip}/joomla/administrator/language/ => Directory listing
[####################] - 26s     4614/4614    175/s   http://{shenron_ip}/joomla/administrator/logs/ 
[####################] - 13s     4614/4614    353/s   http://{shenron_ip}/joomla/layouts/plugins/ => Directory listing
[####################] - 10s     4614/4614    469/s   http://{shenron_ip}/joomla/libraries/src/ => Directory listing
[####################] - 9s      4614/4614    501/s   http://{shenron_ip}/joomla/administrator/modules/ => Directory listing
[####################] - 8s      4614/4614    613/s   http://{shenron_ip}/joomla/libraries/vendor/ => Directory listing
[####################] - 7s      4614/4614    633/s   http://{shenron_ip}/joomla/media/system/ => Directory listing
[####################] - 0s      4614/4614    29019/s http://{shenron_ip}/joomla/administrator/templates/ => Directory listing   
```