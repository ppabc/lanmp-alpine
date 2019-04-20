FROM php:7.2.4-cli-alpine3.7
RUN apk update && apk upgrade
RUN apk add m4 autoconf make gcc g++ linux-headers
RUN pecl install swoole-4.2.1
RUN docker-php-ext-enable swoole
CMD ["php","-m"]
