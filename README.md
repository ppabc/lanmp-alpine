# lanmp-alpine

alpine系统apk add方式安装lanmp环境，快速安装

详细方法见 (https://aqzt.com/5415.html)

创建 MYSQL master 容器

docker run –name mysql-master1 -p 3316:3306 -v /data1:/data -d ppabc/lanmp-alpine:mysql

创建 MYSQL slave 容器

docker run –name mysql-master2 -p 3326:3306 -v /data2:/data -d ppabc/lanmp-alpine:slave

mkdir -p /tmp/rpm /data/nginx/conf/vhost /data/php /data/nginx/logs /data/nginx/run /data/wwwroot/default

docker run -d --name mysql -v /data:/data --net=host -it ppabc/lanmp-alpine:php5

docker run -d --name php5 -v /data:/data --net=host -it ppabc/lanmp-alpine:php7

docker run -d --name nginx -v /data:/data --net=host -it ppabc/lanmp-alpine:nginx
