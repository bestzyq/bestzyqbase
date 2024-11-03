---
title: Mediawiki-nginx伪静态设置
date: 2024-11-03 17:30:17
tags: 
- Nginx
- Mediawiki
---
```
location ~ ^\/.+$ {if ($request_uri ~ ^/cache) { break; }if ($request_uri ~ ^/docs) { break; }if ($request_uri ~ ^/extensions) { break; }if ($request_uri ~ ^/images) { break; }if ($request_uri ~ ^/includes) { break; }if ($request_uri ~ ^/languages) { break; }if ($request_uri ~ ^/maintenance) { break; }if ($request_uri ~ ^/mw-config) { break; }if ($request_uri ~ ^/resources) { break; }if ($request_uri ~ ^/skins) { break; }if ($request_uri ~ ^/tests) { break; }if ($request_uri ~ ^/vendor) { break; }if ($request_uri ~ ^/index\.php) { break; }rewrite ^/(.+)$ /index.php?title=$1 last;}
```