
FROM php:7.4-apache

RUN a2dissite 000-default

WORKDIR /var/www/html

RUN apt-get update && apt-get install -y git zip unzip libzip-dev
RUN apt-get install -y wget libjpeg-dev libfreetype6-dev
RUN apt-get install -y  libmagick++-dev \
libmagickwand-dev \
libpq-dev \
libfreetype6-dev \
libjpeg62-turbo-dev \
libpng-dev \
libwebp-dev \
libxpm-dev

RUN docker-php-ext-configure gd --with-freetype=/usr/include/ --with-jpeg=/usr/include/
RUN docker-php-ext-install -j$(nproc) gd zip bcmath sockets mysqli pdo_mysql # mysqli と pdo_mysql はどっちかで良さそう

RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php -- --version=1.10.21 && mv /usr/bin/composer.phar /usr/bin/composer
