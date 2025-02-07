# JavaScript IRC Client

HTML embed code block with jsircclient.js that implements html/javascript IRC client on a website.

Requirements (debian linux server):
 * Apache HTTP Server 2.4.47 or later with mod_proxy, mod_proxy_http and mod_rewrite enabled.
 * Websockify to convert websocket to normal raw local socket.

Install:
```
sudo apt install apache2
sudo apt install websockify
```

Enable apache proxy/rewrite mods:
```
sudo a2enmod proxy
sudo a2enmod proxy_http
sudo a2enmod rewrite
```

Enable websockify websocket mirror:
```
sudo websockify -D --log-file=/var/log/websockify.log 6668 localhost:6667
```

Apache site enable websocket rewrite:
```
RewriteEngine On
RewriteCond %{HTTP:Upgrade} =websocket [NC]
RewriteRule /wsirc ws://localhost:6668/ [P,L]
```
