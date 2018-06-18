FROM alpine:3.7
MAINTAINER ppabc <ppabc@qq.com>
##RUN echo "https://mirrors.aliyun.com/alpine/v3.7/main" > /etc/apk/repositories
##RUN echo "https://mirrors.aliyun.com/alpine/v3.7/community" >> /etc/apk/repositories

COPY startup.sh /startup.sh
COPY my.cnf /etc/mysql/my.cnf

RUN set -x \
	&& addgroup -g 82 -S mysql \
	&& adduser -u 82 -D -S -G mysql mysql \
	&& chmod 777 /tmp

RUN apk add --update mariadb mariadb-client && rm -f /var/cache/apk/*
RUN apk --no-cache add tzdata  && \
    ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime && \
    echo "Asia/Shanghai" > /etc/timezone 

EXPOSE 3306
CMD ["/startup.sh"]
