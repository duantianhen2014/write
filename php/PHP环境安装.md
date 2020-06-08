## PHP环境安装

1. ubuntu环境：

   apt-get update
   apt-get upgrade
   apt install php7.2-cli
   apt install php7.2-opcache
   apt install php7.2-curl
   apt install php7.2-gd
   apt install php7.2-json
   apt install php7.2-mysql
   apt install php7.2-xml
   apt install php7.2-zip
   apt install php7.2-fpm
   apt install php7.2-redis
   apt install php7.2-mbstring

   apt install php-bcmatch

   ##安装dev版本为了得到phpize方便后期编译安装扩展
   apt install php7.2-dev
   php -m
   /etc/init.d/php7.2-fpm status
   phpize -v