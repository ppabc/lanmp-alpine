FROM alpine:3.7
MAINTAINER ppabc <ppabc@qq.com>
##RUN echo "https://mirrors.aliyun.com/alpine/v3.7/main" > /etc/apk/repositories
##RUN echo "https://mirrors.aliyun.com/alpine/v3.7/community" >> /etc/apk/repositories

RUN set -x \
	&& mkdir -p /var/lib/mysql/ /run/mysqld /data/mysql/data/ /data/mysql/logs/ \
	&& addgroup -g 82 -S mysql \
	&& adduser -u 82 -D -S -G mysql mysql \
	&& chown -R root:mysql /data/mysql \
	&& chown -R root:mysql /run/mysqld \
	&& chmod 777 /tmp
	
WORKDIR /data
VOLUME /data
COPY startup.sh /startup.sh
RUN apk add --update mariadb mariadb-client && rm -f /var/cache/apk/*
COPY my.cnf /etc/mysql/my.cnf

EXPOSE 3306
CMD ["/startup.sh"]
