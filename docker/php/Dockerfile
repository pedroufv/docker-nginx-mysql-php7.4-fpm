FROM php:7.4-fpm-alpine

# 1. install Additional dependencies
RUN apk update && apk add --no-cache \
    build-base shadow vim curl \
    php7 \
    php7-fpm \
    php7-common \
    php7-pdo \
    php7-pdo_mysql \
    php7-mysqli \
    php7-mcrypt \
    php7-mbstring \
    php7-xml \
    php7-openssl \
    php7-json \
    php7-phar \
    php7-zip \
    php7-gd \
    php7-dom \
    php7-session \
    php7-zlib

# 2. install nodejs and npm
RUN apk add --update npm

# 3. install php extensions
RUN docker-php-ext-install pdo pdo_mysql
RUN docker-php-ext-enable pdo_mysql

# 4. composer
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# 5. remove Cache
RUN rm -rf /var/cache/apk/*

# 5. add UID '1000' to www-data
ARG uid
RUN usermod -u $uid www-data

# 6. set working directory
WORKDIR /var/www

# 7. change current user to www
USER www-data

# 8. expose port 9000 and start php-fpm server
EXPOSE 9000
CMD ["php-fpm"]
