FROM php:7.2.4-cli-alpine3.7
RUN apk update && apk upgrade
RUN apk add m4 autoconf make gcc g++ linux-headers
RUN apk --update add \
        libpng-dev \
		libpng-utils \
		libpng \
		imagemagick \
        php7 \
        php7-common \
        php7-bcmath \
        php7-dom \
        php7-ctype \
        php7-curl \
        php7-fpm \
        php7-gd \
        php7-iconv \
        php7-intl \
        php7-json \
        php7-mbstring \
        php7-mcrypt \
        php7-opcache \
		php7-memcached \
		php7-apcu \
		php7-imagick \
		php7-imagick-dev \
        php7-openssl \
        php7-pdo \
        php7-mysqlnd \
        php7-pdo_mysql \
		php7-mysqli \
        php7-pdo_pgsql \
        php7-pdo_sqlite \
        php7-phar \
        php7-posix \
        php7-session \
        php7-soap \
        php7-xml \
		php7-simplexml \
        php7-zip \
    && rm -rf /var/cache/apk/*
RUN pecl install swoole-4.2.1
RUN docker-php-ext-enable swoole
CMD ["php-fpm7", "-F"]
