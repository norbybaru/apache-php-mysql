FROM php:7.0-fpm
LABEL maintainer="norbybaru@gmail.com"

RUN apt-get update \
    && apt-get install -y libpq-dev libmcrypt-dev libfreetype6-dev libjpeg62-turbo-dev libpng-dev zlib1g-dev \
    && docker-php-ext-install -j$(nproc) iconv mcrypt \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) gd \
    && docker-php-ext-install zip mbstring \
    && docker-php-ext-install pdo pdo_mysql mysqli

RUN curl -sS https://getcomposer.org/installer | php
RUN mv composer.phar /usr/local/bin/composer

CMD ["php-fpm"]
