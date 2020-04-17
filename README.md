# Docker: PHP 7.4 + NGNIX + MySQL

environment to run laravel applications with nginx, php7.4-fpm, mysql and phpmyadmin

## Docker Compose
> Configure DOCKER_UID in .env
- Change settings in `.env` e `.env.testing`
- Buil docker images `docker-compose build`
- Up services `docker-compose up -d`
- Install PHP dependencies `docker-compose exec app composer install`
- Install JS dependencies `docker-compose exec app /bin/sh -c "npm install && npm run dev"`
- Apply migrations `docker-compose exec app php artisan migrate`
- Check logs `docker-compose logs -t`

### Docker tips
- Build and up services `docker-compose up -d --buld`
- Up minimum `docker-compose up -d app`
- Shell access `docker-compose exec app /bin/sh`
- Filter logs by service `docker-compose logs -t app`
- Check logs in runtime `docker-compose logs -tf app`

### Makefile

* `make build` initializes the containers, installs dependencies and performs migrations
* `make clean` clear cache and compiled files
* `make composer` installs php dependencies
* `make down` turns off containers
* `make logs` displays 100 latest application log records
* `make migrate` run migrations 
* `make npm` install js dependencies
* `make test` run tests
* `make up` turns on containers
