FROM composer:2.2 as composer_step

FROM php:8-fpm

# Copy composer to php:8-fpm dir
COPY --from=composer_step /usr/bin/composer /usr/bin/composer

RUN composer --version && php -v

ARG ARG_UID=1000
ARG ARG_GID=1000

# Create a group and user for this container
# The GID and UID should match the UID and GID of the user running docker.
# Run `id` commmand on the terminal to find out the UID and GID value.
RUN groupadd -g ${ARG_GID} app
RUN useradd app -u ${ARG_UID} -g ${ARG_GID} -s /bin/bash

RUN apt-get update && \
    apt-get install -y libzip-dev \
        zip \
    && docker-php-ext-install zip

RUN docker-php-ext-install pdo_mysql