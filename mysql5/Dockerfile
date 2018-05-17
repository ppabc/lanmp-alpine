FROM alpine:3.7
MAINTAINER ppabc <ppabc@qq.com>
##RUN echo "https://mirrors.aliyun.com/alpine/v3.7/main" > /etc/apk/repositories
##RUN echo "https://mirrors.aliyun.com/alpine/v3.7/community" >> /etc/apk/repositories

ENV TZ='CST'

COPY startup.sh /startup.sh
COPY my.cnf /etc/my.cnf

RUN set -x \
&& apk update && apk add tzdata \
&& apk add --update mariadb mariadb-client \
&& ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \ 
&& echo "Asia/Shanghai" > /etc/timezone \
&& rm -f /var/cache/apk/* \
&& chmod +x /startup.sh \
&& addgroup -g 82 -S mysql \
&& adduser -u 82 -D -S -G mysql mysql \
&& chmod 777 /tmp

EXPOSE 3306
CMD ["/startup.sh"]

