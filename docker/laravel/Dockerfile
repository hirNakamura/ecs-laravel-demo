FROM php:8.0-fpm

COPY ./src /app

WORKDIR /app

ENV TZ Asia/Tokyo

# install Composer
COPY --from=composer:2.0 /usr/bin/composer /usr/bin/composer

# install Library
RUN apt-get update && \
	apt-get install -y git unzip libzip-dev libicu-dev libonig-dev && \
	docker-php-ext-install intl pdo_mysql zip bcmath && composer install

RUN php artisan cache:clear \
     && php artisan config:clear \
     && php artisan route:clear \
     && php artisan view:clear

# config file COPY
COPY ./docker/laravel/php.ini /usr/local/etc/php/php.ini

WORKDIR /app