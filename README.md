# docker ubuntu nginx-php-fpm-mariadb

## git clone

```shell
$ git clone git@github.com:Kenj-I/docker_nginx_phpfpm_mariadb_dev.git
```

## init

```shell
$ cd docker-nginx_phpfpm_mariadb_dev
$ sh init.sh
```

## write env

.env and build/envfile

if use nginx_proxy, set virtualhost and your hosts

```.env
//.env

VIRTUAL_HOST=
HOST_DB_PORT=
COMPOSE_PROJECT_NAME=
```

```envfile
//./build/envfile
MYSQL_ROOT_PASSWORD=
MYSQL_DATABASE=
MYSQL_USER=
MYSQL_PASSWORD=

DATABASE_HOST=
DATABASE_NAME=
DATABASE_USER=
DATABASE_PASSWORD=
```

## usage

UP

```shell
$ cd docker_nginx_phpfpm_mariadb_dev
$ docker-compose up --no-start
$ docker-compose up -d
```

```shell
$ docker-compose stop
```
