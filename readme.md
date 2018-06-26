<p align="center"><img src="https://laravel.com/assets/img/components/logo-laravel.svg"></p>

<p align="center">
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/d/total.svg" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/v/stable.svg" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/license.svg" alt="License"></a>
</p>

# Install

```sh
copy .env.example .env          # set setings for database in .env
composer install
php artisan key:generate
php artisan migrate:fresh --seed
npm install
```

# Development

## Linux

```sh
npm run hot
php artisan serve   # open site http://localhost:8000
```

## Windows

Install <a href="https://ospanel.io/">OpenServer</a>.<br>
Install laravel.<br>
Open site from OpenServer.

```
npm run hot     # for start frontend
```

# Deploy

```sh
php artisan deploy
```

Смотри файл config/deploy.php ! секцию hosts. Если указан stage, то
``` 
php artisan deploy {stage}
```


# Generate helpers

```
php artisan ide-helper:meta && php artisan ide-helper:generate && php artisan sleepingowl:ide:generate
```
