FROM php:7.1-fpm

RUN apt-get update \
    && apt-get -y install git wget zip sshpass libmcrypt-dev libxml2-dev \
    && pecl channel-update pecl.php.net \
    && pecl install xdebug-2.7.2 \
    && docker-php-ext-install -j$(nproc) bcmath mcrypt iconv pdo_mysql mbstring xml tokenizer \
    && docker-php-ext-enable xdebug

# Composer install.
COPY --from=composer /usr/bin/composer /usr/bin/composer
ENV COMPOSER_ALLOW_SUPERUSER 1
ENV COMPOSER_HOME /composer
ENV PATH $PATH:/composer/vendor/bin
