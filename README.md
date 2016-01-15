Dockerized PHP development stack [![Build Status](https://travis-ci.org/lagun4ik/docker-php-dev-stack.svg)](https://travis-ci.org/lagun4ik/docker-php-dev-stack)
--------------------------

## Include

* [Nginx 1.9.9](http://nginx.org/)
 * [ngx_pagespeed](https://github.com/pagespeed/ngx_pagespeed)
 * [nginx-upload-progress-module](https://github.com/masterzen/nginx-upload-progress-module)
* [PHP7.0-FPM](http://php-fpm.org/)
 * [Installed php modules](#installed-php-modules)
 * [Composer](https://getcomposer.org/)
* [MariaDB 3.2](https://mariadb.org/)
* [MongoDB 3.2](http://www.mongodb.org/)
* [Memcached 1.4.25](http://memcached.org/)
* [Redis 3.0.6](http://redis.io/)

## Requirements

* Build - 512MB RAM + 1GB of swap
* Run  - 512MB RAM`

## Run

```bash
docker-compose -p php-dev-stack up -d
```

## Show services

```bash
docker-compose -p php-dev-stack ps
```

## Composer

Enter the name of your container.

```bash
#Show container names
docker ps | grep -P "\s([^\s]*php-fpm[^$]\s)|(IMAGE)"

#Run bash in container
docker run --rm -it \
  --volumes-from php-dev-stack_data -w /var/www/ \
  YOU_IMAGE_NAME bash
```


## Restart nginx

Enter the name of your container.

```bash
#Show image name
docker ps | grep -P "\s([^\s]*nginx[^\s]*$)|(NAMES$)"

#Restart nginx
docker exec -t YOU_CONTAINER_NAME bash -c "service nginx restart"
```

## Look at the logs

```bash
# all logs
docker-compose -p php-dev-stack logs

# specific service
docker-compose -p php-dev-stack logs nginx
```
