FROM php:7.4-apache

RUN apt-get update -y

RUN apt-get install -y --no-install-recommends --assume-yes --quiet ca-certificates\
        curl\
        git\
        g++\
        gnupg2\
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        libyaml-dev \
        libzip-dev \
        zip \
    && docker-php-ext-install zip\
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-install pdo mysqli pdo_mysql

RUN curl -sSk https://getcomposer.org/installer | php -- --disable-tls && \
   mv composer.phar /usr/local/bin/composer

RUN apt-get install -y npm

RUN npm i npm@latest -g

RUN pecl install yamL

RUN usermod -u 1000 www-data

RUN a2enmod rewrite

WORKDIR /var/www/html