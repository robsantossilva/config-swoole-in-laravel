<p align="center" style="display:flex; justify-content: center;">

<img src="https://res.cloudinary.com/dtfbvvkyp/image/upload/v1566331377/laravel-logolockup-cmyk-red.svg" width="180">

<img src="https://avatars3.githubusercontent.com/u/8121270?s=200&v=4" width="100">

</p>

<p align="center">
<a href="https://travis-ci.org/laravel/framework"><img src="https://travis-ci.org/laravel/framework.svg" alt="Build Status"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/d/total.svg" alt="Total Downloads"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/v/stable.svg" alt="Latest Stable Version"></a>
<a href="https://packagist.org/packages/laravel/framework"><img src="https://poser.pugx.org/laravel/framework/license.svg" alt="License"></a>
</p>

## Configurando Swoole no Laravel

#### Prérequisitos
Laravel >= 5.6

#### Instalando a extensão
``` bash
$ pecl install swoole

$ touch /usr/local/etc/php/conf.d/swoole.ini && \
    echo 'extension=swoole.so' > /usr/local/etc/php/conf.d/swoole.ini
```

#### Instale o pacote
``` bash
composer require swooletw/laravel-swoole
```

#### Gerando arquivos de configuração
``` bash
$ php artisan vendor:publish --tag=laravel-swoole
```

/config/swoole_http.php
/config/swoole_websocket.php
/routes/websocket.php

#### Comandos

> O swoole_http_server pode ser executado apenas no ambiente cli, e este pacote fornece comandos artesanais convenientes para gerenciá-lo.
> Por padrão, você pode visitar seu site em http://127.0.0.1:1215

> `php artisan swoole:http {start|stop|restart|reload|infos}`

| Command | Description |
| --------- | --------- |
| `start` | Start Laravel Swoole, list the processes by *ps aux&#124;grep swoole* |
| `stop` | Stop Laravel Swoole |
| `restart` | Restart Laravel Swoole |
| `reload` | Reload all worker process(Contain your business & Laravel/Lumen codes), excluding master/manger process |
| `infos` | Show PHP and Swoole basic miscs infos(including PHP version, Swoole version, Laravel version, server status and PID) |

Agora, você pode executar o seguinte comando para iniciar o servidor HTTP Swoole.

```
$ php artisan swoole:http start
```


Você pode mostrar suas informações básicas executando

```
$ php artisan swoole:http infos
```

```
+-----------------+-------------------------------------------------------------+
| Name            | Value                                                       |
+-----------------+-------------------------------------------------------------+
| PHP Version     | 7.1.14                                                      |
| Swoole Version  | 2.1.1-alpha                                                 |
| Laravel Version | 5.6.17                                                      |
| Server Status   | Online                                                      |
| Listen IP       | 127.0.0.1                                                   |
| Listen Port     | 1215                                                        |
| Websocket Mode  | On                                                          |
| PID             | 3956                                                        |
| Log Path        | /Users/Albert/Projects/laravel/storage/logs/swoole_http.log |
+-----------------+-------------------------------------------------------------+
```
