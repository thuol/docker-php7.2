# docker-php7.2
使用docker搭建的nginx-php7.2环境  
本环境只用 nginx php 无其他服务。mysql redis等可以使用本地机器上的服务。或者自行更改 docker-compose.yml 配置文件添加

## 目录
```
build                   打包docker-php7.2 的配置。如果环境不满足使用，可以自行更改源码打包成自己的docker镜像  
php72                   项目目录
  ├ nginx               nginx服务器配置
  ├ .env                目录映射配置
  └ docker-compose.yml  启动配置
```

## 配置
- 目录映射  
在 .env 文件中更改参数 `coderoot` 为自己本地的项目目录
- 多nginx服务配置  
在 /php72/nginx 目录中配置多个nginx.conf ，此目录与本地nginx配置目录相当。
- 默认端口  
默认将本地的 8080 端口映射到 docker 的80端口。灵活使用可以自行在 docker-compose.yml 更改。

## 使用
进入 /php72 目录
```
docker-compose up       # 启动
docker-compose up -d    # 后台启动
docker-compose restart  # 重启
docker-compose stop     # 停止
```