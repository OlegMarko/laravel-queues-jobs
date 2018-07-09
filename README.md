<p align="center"><img src="https://laravel.com/assets/img/components/logo-laravel.svg"></p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/d/total.svg" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/v/stable.svg" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/license.svg" alt="License"></a>
</p>

## Laravel QUEUE

- run command step by step in your terminal
```
    git clone https://github.com/OlegMarko/laravel-queues-jobs.git
    cd laravel-queues-jobs
    composer install
    cp .env.example .env
    touch database/database.sql
    php artisan migrate
    php artisan serve
    php artisan queue:work
```
[test route](http://127.0.0.1:8000)

** Messages about running jobs are written to the `storage/logs/laravel.log` file

## Laravel Supervisor conf

`sudo apt install supervisor`

`cd /etc/supervisor/conf.d`

`sudo nano laravel-worker.log`

```
[program:laravel-worker]
#process_name=%(program_name)s_%(process_num)02d
command=php /var/www/laravel-queues-jobs/artisan queue:work --sleep=3 --tries=3
autostart=true
autorestart=true
user=root
numprocs=1
redirect_stderr=true
stdout_logfile=/var/log/supervisor/laravel-worker.log
```

`sudo supervisorctl reread`

`sudo supervisorctl update`

start process

`sudo supervisorctl start laravel-worker`

stop process

`sudo supervisorctl stop laravel-worker`

## License

The Laravel framework is open-sourced software licensed under the [MIT license](https://opensource.org/licenses/MIT).
