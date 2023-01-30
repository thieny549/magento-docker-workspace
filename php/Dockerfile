FROM php:8.1.5-fpm-bullseye

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libzip-dev \
        libpq-dev \
        zip \
        libxslt-dev \
        gnupg \
        gnupg1 \
        gnupg2

RUN docker-php-ext-install mysqli \
    && docker-php-ext-install pdo_mysql \
    && docker-php-ext-configure pgsql -with-pgsql=/usr/local/pgsql \
    && docker-php-ext-install bcmath \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install zip \
    && docker-php-ext-install xsl \
    && docker-php-ext-install pgsql \
    && docker-php-ext-install pdo_pgsql \
    && docker-php-ext-install intl \
    && docker-php-ext-install exif \
    && docker-php-ext-install soap \
    && docker-php-ext-install sockets
    
RUN pecl install xdebug-3.1.3 \
    && docker-php-ext-enable xdebug

RUN cp "$PHP_INI_DIR/php.ini-development" "$PHP_INI_DIR/php.ini"

RUN curl -o /tmp/composer-setup.php https://getcomposer.org/installer
RUN php /tmp/composer-setup.php --install-dir=/usr/local/bin --filename=composer \
    && rm -rf /tmp/composer-setup.php
