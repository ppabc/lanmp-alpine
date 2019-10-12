FROM php:7.2.17-fpm-alpine3.9
LABEL maintainer="ppabc <ppabc@qq.com>" version="1.0"
ENV SWOOLE_VERSION=4.1.2 \
    REDIS_VERSION=4.0.2

#Timezone and lib
RUN apk add -U tzdata \
    && cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
    && apk del tzdata

RUN set -ex \
        && cd /tmp \
        && curl -SL "https://github.com/swoole/swoole-src/archive/v${SWOOLE_VERSION}.tar.gz" -o swoole.tar.gz \
        && curl -SL "http://pecl.php.net/get/redis-${REDIS_VERSION}.tgz" -o redis.tgz \
        && ls -alh \
        && apk update \
        && apk add --no-cache --virtual .phpize-deps $PHPIZE_DEPS \
        # for swoole ext
        && apk add --no-cache libaio \
         linux-headers \
         libaio-dev \
	 hiredis-dev \
         openssl-dev \
         libstdc++ \
         librdkafka-dev \
        # php extension: redis
        && pecl install redis.tgz \
        && docker-php-ext-enable redis \
        # php extension: pdo_mysql
        && docker-php-ext-install pdo_mysql \
        # php extension: bcmath
        && docker-php-ext-install bcmath \
        # php extension: swoole
        && cd /tmp \
        && mkdir -p swoole \
        && tar -xf swoole.tar.gz -C swoole --strip-components=1 \
        && rm swoole.tar.gz \
                && ( \
                    cd swoole \
                    && phpize \
                    && ./configure --enable-async-redis --enable-mysqlnd --enable-coroutine --enable-openssl \
                    && make -j$(nproc) && make install \
                ) \
                && rm -r swoole \
                && docker-php-ext-enable swoole \
        && apk del .phpize-deps
COPY so/*.so /usr/local/lib/php/extensions/no-debug-non-zts-20170718/
COPY conf/*.ini /usr/local/etc/php/conf.d/