FROM aqzt/docker-alpine
LABEL maintainer="aqzt.com (ppabc@qq.com)"
##RUN echo "https://mirrors.aliyun.com/alpine/v3.7/main" > /etc/apk/repositories
##RUN echo "https://mirrors.aliyun.com/alpine/v3.7/community" >> /etc/apk/repositories

RUN apk --no-cache add tzdata  && \
    ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    echo "Asia/Shanghai" > /etc/timezone 

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

COPY php.ini /etc/php7/conf.d/50-setting.ini
COPY php-fpm.conf /etc/php7/php-fpm.conf

#RUN ln -s /usr/bin/php7 /usr/bin/php

EXPOSE 9002

CMD ["php-fpm7", "-F"]
