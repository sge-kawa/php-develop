FROM php:7.2-fpm

RUN apt-get update \
    && apt-get -y install git wget zip sshpass libmcrypt-dev libxml2-dev \
    && pecl install xdebug \
    && docker-php-ext-install -j$(nproc) bcmath iconv pdo_mysql mbstring xml tokenizer \
    && docker-php-ext-enable xdebug

# Composer install.
COPY --from=composer /usr/bin/composer /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin
