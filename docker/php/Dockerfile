FROM composer:2.2 as composer_step

FROM php:8-fpm

# Copy composer to php:8-fpm dir
COPY --from=composer_step /usr/bin/composer /usr/bin/composer

RUN composer --version && php -v

RUN apt-get update && \
    apt-get install -y libzip-dev \
        zip \
    && docker-php-ext-install zip

RUN docker-php-ext-install pdo_mysql