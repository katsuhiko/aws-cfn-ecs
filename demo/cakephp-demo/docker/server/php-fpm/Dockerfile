FROM php:7.4-fpm-buster

RUN apt-get update

RUN apt-get install -y git libzip-dev zip unzip \
    && docker-php-ext-install zip

RUN docker-php-ext-install pdo_mysql

RUN apt-get install -y libicu-dev \
    && docker-php-ext-configure intl \
    && docker-php-ext-install intl

RUN apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install gd

RUN docker-php-ext-install opcache

COPY ./ /var/www/html
RUN cp -f /var/www/html/config/app_local.example.php /var/www/html/config/app_local.php

WORKDIR /var/www/html

RUN php composer.phar install --no-dev --optimize-autoloader

RUN chmod -R 777 tmp
RUN chmod -R 777 vendor
