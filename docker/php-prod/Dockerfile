FROM php:8.0.0-fpm

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        zlib1g-dev \
        libzip-dev \
        unzip \
        nano\
        librsvg2-bin\
     && docker-php-ext-install -j$(nproc) iconv \
        && docker-php-ext-configure gd --with-freetype --with-jpeg \
        && docker-php-ext-install -j$(nproc) gd \
        && docker-php-ext-install exif \
        && rm -rf /var/lib/apt/lists/*

RUN pecl install -o -f redis \
    &&  rm -rf /tmp/pear \
    &&  docker-php-ext-enable redis

RUN apt-get update && apt-get install -y cron

RUN docker-php-ext-install mysqli pdo pdo_mysql

#COPY opcache.ini /usr/local/etc/php/conf.d/

ADD app /app

RUN apt-get update
RUN chmod 777 /app/public
RUN chmod -R 755 /app/storage
WORKDIR /app