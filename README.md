```
  ___                   _                             _ 
 / __)          _      | |                           | |
| |__ ____  ___| |_    | | ____  ____ ____ _   _ ____| |
|  __) _  |/___)  _)   | |/ _  |/ ___) _  | | | / _  ) |
| | ( ( | |___ | |__   | ( ( | | |  ( ( | |\ V ( (/ /| |
|_|  \_||_(___/ \___)  |_|\_||_|_|   \_||_| \_/ \____)_|                                             

```
> 🚀[fast-laravel](https://packagist.org/packages/toxmc/fast-laravel). is a package that made you `laravel` application fast.

#### install 
first you mush install [composer](https://getcomposer.org/)

add require info into composer.json and execute `composer install`
```
"require": {
    "toxmc/fast-laravel":"dev-master"
},
```
or
```bash
composer require "toxmc/fast-laravel:dev-master" -vvv
```

add `Service Provider` into `config/app.php`
```
[
    'providers' => [
        FastLaravel\Http\LaravelServiceProvider::class,
    ],
]
```

Publish configuration and binaries.
```
$ php artisan vendor:publish --tag=fast-laravel
or
$ php artisan http publish

```
config configuration
```
$ php artisan http config
```
start server
```
$ php fast http:start
```

#### command：
```
php artisan http {action : publish|config|infos}.
```
* publish:Publish configuration and binaries.
* config:Generate command(fast) configuration information
* infos:show information

```
php fast http::{action : start|stop|restart|reload|infos} {-d|--daemonize : Whether run as a daemon for start & restart}.
```
* start:start server
* stop:stop server
* restart:restart server
* reload:reload server
* infos:show information

#### supervisor manage services

install
```
brew install supervisor
```

start
```
supervisord -c supervisor/supervisor.conf
```

manage
```
[xmc@mc fast-laravel (master ✗)]$ supervisorctl -c supervisor/supervisor.conf
fast-laravel-monitor             RUNNING   pid 18131, uptime 0:03:11

supervisor> help

default commands (type help <topic>):
=====================================
add    exit      open  reload  restart   start   tail   
avail  fg        pid   remove  shutdown  status  update 
clear  maintail  quit  reread  signal    stop    version

supervisor> status
fast-laravel-monitor             RUNNING   pid 29146, uptime 3:03:36
```

#### hot reload（mac）

1：edit `.env` and restart server
```
SWOOLE_HOT_RELOAD=true
```
or edit `swoole_http.php`
```
'hot_reload' => env('SWOOLE_HOT_RELOAD', true),
```


2：fswatch
```
brew install fswatch

[xmc@mc fast-laravel (master ✗)]$ sh fswatch.sh /Users/xmc/PhpstormProjects/iizhu/api
Starting fswatch...
File /Users/xmc/PhpstormProjects/iizhu/api/app/Service/TestService.php has been modified.
Reloading swoole_http_server...
> success
File /Users/xmc/PhpstormProjects/iizhu/api/app/Service/TestService.php has been modified.
Reloading swoole_http_server...
> success
```

#### Alternative
* [laravel-swoole](https://github.com/swooletw/laravel-swoole)
#### Alternative Framework
* [Swoft](https://www.swoft.org/)
* [easyswoole](http://www.easyswoole.com/)
* [hyperf](http://www.hyperf.io/)

#### Others
* Q群:190349019