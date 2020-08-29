# What is thinkphp5
The thinkphp5 image containes Nginx, PHP, PHP-FPM. It can facilitate you to quickly deploy small and medium php projects (including php web and php websocket).

# How to use this image
The thinkphp5 image exposes port 80 and mounts `/app` directory.  
## Exposing external port
```
$ docker run -p 80:80 -d your-pull-image
```
Then you can hit `http://localhost` or `http://host-ip` in your browser.

## Exposing with your thinkphp5 project
```
$ docker run -p 80:80 -v /proect_location:/app -d your-pull-image
```
The web homepage defaults to `index.php` and `index.html`. The configuration of thinkphp is configured in accordance with the [thinkphp5 complete development manual](). You can easily configure the mysql connection or redis connection of your project.

## How to run WebSocket
You can build again based on this image, change `ENTRYPOINT` to `php-fpm7 && nginx && WebSocket script && tail -f /dev/null`, If WebSocket is running in the foreground, `ENTRYPOINT` is `php-fpm7 && nginx && websocket script`.

# License
MIT.