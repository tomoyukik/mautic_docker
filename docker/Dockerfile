# https://qiita.com/ggg-mzkr/items/8607de72f672efbcde34

FROM php:7.4-apache

RUN a2dissite 000-default

WORKDIR /var/www/html

RUN apt-get update && apt-get install -y git zip unzip
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
RUN docker-php-ext-install -j$(nproc) gd
RUN apt-get install -y libzip-dev
RUN docker-php-ext-install zip bcmath sockets

RUN cd /usr/bin && curl -s http://getcomposer.org/installer | php -- --version=1.10.21 && mv /usr/bin/composer.phar /usr/bin/composer
