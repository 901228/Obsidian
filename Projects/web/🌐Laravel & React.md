---
title : 🌐Laravel & React
date : 2023-05-05_Fri 12:28
aliases : [laravel, react]
---
Source Type :: #📥/📄 <br>
Note Type :: #📝 <br>
Topics :: [[🌐網頁 Moc]]<br>
Parent Link :: [[🌐網頁 Moc]]<br>

---
# Laravel & React

1. For Laravel 7+ projects:
```bash
composer require laravel/ui
php artisan ui react
npm install
npm run dev
npm run watch
```

2. add
```html
<head>
	...
    @viteReactRefresh
    @vite(['resources/css/app.css', 'resources/js/app.js'])
    ...
</head>
```
to the `.blade.php` file

3. complete => you can use react on laravel !