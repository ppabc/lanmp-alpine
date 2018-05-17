FROM alpine:3.7
MAINTAINER ppabc <ppabc@qq.com>
##RUN echo "https://mirrors.aliyun.com/alpine/v3.7/main" > /etc/apk/repositories
##RUN echo "https://mirrors.aliyun.com/alpine/v3.7/community" >> /etc/apk/repositories

ENV	TZ='CST'

RUN set -x \
	&& addgroup -g 82 -S mysql \
	&& adduser -u 82 -D -S -G mysql mysql \
	&& chmod 777 /tmp
	
COPY startup.sh /startup.sh
RUN apk add --update mariadb mariadb-client && rm -f /var/cache/apk/*  && chmod +x /startup.sh
COPY my.cnf /etc/my.cnf

EXPOSE 3306
CMD ["/startup.sh"]
