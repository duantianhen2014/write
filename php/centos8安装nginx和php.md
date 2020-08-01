## centos8安装nginx和php

#### 更新

yum -y upgrade

sudo dnf update -y

#### php

dnf search php

dnf module list php

sudo dnf module reset php

dnf module list php

sudo dnf module enable php:7.3

dnf module list php

sudo dnf module install php:7.3

php -v

php -m

sudo dnf install -y php php-cli php-common

php -v

dnf install -y php-fpm

sudo dnf install -y php-fpm

sudo dnf install -y php-mysqlnd

php -m

sudo dnf install -y php-zip

sudo dnf install -y php-bcmatch

sudo dnf install -y php-bcmath

#### composer

curl -sS https://getcomposer.org/installer |php

sudo mv composer.phar /usr/local/bin/composer

composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/

#### nginx

cd /etc/yum.repos.d/

ls -la

vim nginx.repo

http://nginx.org/en/linux_packages.html#RHEL-CentOS 官方安装文档

yum list | grep nginx

yum -y install nginx

nginx -v

#### redis

dnf module list redis

sudo dnf module install redis

#### git

Yum list | grep git

yum -y install git