---
title : 🌐Laravel & DB
date : 2023-05-05_Fri 11:21
aliases : [laravel, database]
---
Source Type :: #📥/📄 <br>
Source URL :: https://hackmd.io/gr6O3d_HTRSgNlaEjKShVg<br>
Note Type :: #📝 <br>
Topics :: [[🌐網頁 Moc]]<br>
Parent Link :: [[🌐Laravel]]<br>

---
# Laravel & Database
1. goto `.env` file in the laravel project and do some proper modification on
```vim
DB_CONNECTION=mysql   " -> database you use
DB_HOST=127.0.0.1     " -> database host
DB_PORT=3306          " -> database host port
DB_DATABASE=mysql     " -> schema in mysql you want to use
DB_USERNAME=root      " -> database user name
DB_PASSWORD=          " -> database user password
```

2. use `php artisan make:controller <file_name>` to create the controller file<br>
and you can do some qeueries in that file

3. add
```php
Route::get('/<file_name>',
	'App\Http\Controllers\<file_name>@<function_name>');
```
to the `routes/web.php` <br>
then you can view it at `http://localhost/<file_name>`
