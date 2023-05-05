---
title : 🌐Laravel & Apache
date : 2023-05-05_Fri 11:05
aliases : [laravel, apache]
---
Source Type :: #📥/📄<br>
Source URL :: https://tobyisme.gitbook.io/laravel/she-ding-apachejiang-laravel-zhuan-an-run-qi-lai<br>
Note Type :: #📝 <br>
Topics :: [[🌐網頁 Moc]]<br>
Parent Link :: [[🌐網頁 Moc]]<br>

---
# 把 Laravel 和 Apache 串接起來
1. goto
```bash
vi /etc/httpd/conf/httpd.conf/etc/httpd/conf/httpd.conf
(in linux)
or
xampp -> Apache -> Config -> Apache (httpd.conf)
```

---

2. add
```http
<VirtualHost *:80>
    DocumentRoot "<path-to-laravel-projrct>/public"
    <Directory "<path-to-laravel-projrct>/public">
        Options All
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```
in the `httpd.conf` file

---

3. restart the Apache Server