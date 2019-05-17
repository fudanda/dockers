git clone https://github.com/Laradock/laradock.git

> docker

如果报错 （ERROR: Windows named pipe error: 系统找不到指定的文件。 (code: 2)）
1.docker-machine env
2.& "D:\Program Files\Docker Toolbox\docker-machine.exe" env | Invoke-Expression

cd laradock

> 启动

3.docker-compose up -d nginx mysql redis beanstalkd

> 进入目录

4.docker-compose exec workspace bash

> .env

DB_HOST=mysql
REDIS_HOST=redis
QUEUE_HOST=beanstalkd

APP_CODE_PATH_HOST=../wwwroot/

> 进入容器

docker-compose exec php-fpm bash

docker-compose up -d workspace

> docker 命令

docker images #列出本地镜像
docker rmi training/sinatra #删除（在删除镜像之前要先用 docker rm 删掉依赖于这个镜像的所有容器）
docker run -t -i ubuntu:14.04 /bin/bash #
docker commit -m "Added json gem" -a "Docker Newbee" 0b2616b0e5a8 ouruser/sinatra:v2 #更新镜像
docker tag 5db5f8471261 ouruser/sinatra:devel #修改标签
docker build \${dockerfile_dir} #Dockerfile 构建
docker save -o ubuntu_14.04.tar ubuntu:14.04 #保存
docker load --input ubuntu_14.04.tar #导入 #容器
docker ps #查看容器信息
docker rm #删掉容器（-f 删除运行中）
docker inspect #查看指定容器详细信息（可获取 ip，pid 等信息）
docker logs insane_babbage #查看容器 log
docker port CONTAINER [PRIVATE_PORT[/PROTO]] #查看端口映射
docker start|stop|restart insane_babbage #启动终止重启
docker attach insane_babbage #进入后台运行的容器 -d（推荐 nsenter）
docker export 7691a814370e > ubuntu.tar #导出快照
cat ubuntu.tar | sudo docker import - test/ubuntu:v1.0 #导入快照

> docker hub

docker search #搜索镜像
docker pull #下载
docker push #推送（需登录）

> Do not run Composer as root/super user!
> composer install --no-plugins --no-scripts ...
> composer update --no-plugins --no-scripts ...
