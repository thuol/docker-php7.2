FROM centos:7.3.1611

# 初始安装
RUN yum install epel-release -y &&\
    rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm &&\
    rpm -ivh http://nginx.org/packages/centos/7/noarch/RPMS/nginx-release-centos-7-0.el7.ngx.noarch.rpm &&\
    yum -y install make zlib zlib-devel gcc-c++ libtool  openssl openssl-devel &&\
    yum install -y vim tar wget curl bzip2 net-tools lsof sysstat cronie python-setuptools &&\
    yum install pcre pcre-devel -y &&\
    yum -y install nginx-1.12.2 &&\
    yum install php72w php72w-cli php72w-common php72w-fpm php72w-bcmath php72w-gd php72w-mbstring php72w-pdo php72w-mysqlnd php72w-mcrypt php72w-devel -y
RUN mkdir /wwwroot

# 拷贝配置文件
#ADD conf/nginx/default.conf /etc/nginx/conf.d/default.conf
ADD conf/php/php-fpm.conf /etc/php-fpm.conf
ADD conf/php/www.conf /etc/php-fpm.d/www.conf
ADD conf/php/php.ini /etc/php.ini
ADD conf/php/extensions/redis.so /usr/lib64/php/modules/redis.so

# 拷贝启动脚本
ADD start.sh /start.sh
RUN chmod 775 /start.sh

# 启动程序
#CMD ["php-fpm -D"]
#CMD ["nginx"]
#RUN php-fpm -D
#RUN nginx -g "daemon off;"

CMD ["/start.sh"]
