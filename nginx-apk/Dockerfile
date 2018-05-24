FROM alpine:3.7
MAINTAINER ppabc <ppabc@qq.com>
##RUN echo "https://mirrors.aliyun.com/alpine/v3.7/main" > /etc/apk/repositories
##RUN echo "https://mirrors.aliyun.com/alpine/v3.7/community" >> /etc/apk/repositories

RUN apk --update add \
		nginx \
        nginx-mod-http-lua \
		nginx-mod-http-lua-upstream \
    && rm -rf /var/cache/apk/*
 
EXPOSE 80
 
CMD ["nginx", "-g", "daemon off;"]
