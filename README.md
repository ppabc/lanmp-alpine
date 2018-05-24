# lanmp-alpine

# alpine系统apk add方式安装lanmp环境，快速安装

# 采用Docker镜像，可以隔离系统和程序环境，搭建环境标准化，并能快速搭建环境。

# 详细方法见 (https://aqzt.com/5436.html)

## 1.开始快速搭建php环境

创建下需要的目录

mkdir -p /tmp/rpm /mysqldata /data/nginx/conf/vhost /data/php /data/nginx/logs /data/nginx/run /data/wwwroot/default

拉取mysql镜像，并启动

docker run -d --name mysql -v /mysqldata:/data --net=host -it ppabc/lanmp-alpine:mysql

拉取php7镜像，并启动

docker run -d --name php7 -v /data:/data --net=host -it ppabc/lanmp-alpine:php7

拉取php7镜像，并启动

docker run -d --name nginx -v /data:/data --net=host -it ppabc/lanmp-alpine:nginx

## 2.镜像说明

主机WEB目录 /data/wwwroot/default

主机数据库目录  /mysqldata

mysql数据库账号  root  默认密码111111

nginx配置文件目录 /data/nginx/conf/vhost

## 3.镜像地址

docker 镜像地址：https://hub.docker.com/r/ppabc/lanmp-alpine

github 镜像地址：https://github.com/ppabc/lanmp-alpine

## 4.还可以搭建MYSQL主从

创建 MYSQL master 容器

docker run -d --name mysql-master1 -p 3316:3306 -v /data1:/data --net=host  -it ppabc/lanmp-alpine:mysql

创建 MYSQL slave 容器

docker run -d --name mysql-master2 -p 3326:3306 -v /data2:/data --net=host  -it ppabc/lanmp-alpine:slave

## 5.后续还会完善其他

