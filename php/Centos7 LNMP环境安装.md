## Centos7 LNMP环境安装

Centos7：

1. 换源：

   备份：mv /etc/yum.repos.d/CentOS-Base.repo /etc/yum.repos.d/CentOS-Base.repo_bak

   下载：wget -O /etc/yum.repos.d/CentOS-Base.repo http://mirrors.aliyun.com/repo/Centos-7.repo

   更新cache：yum makecache

   更新包：yum -y update

2. 安装nginx

   安装 epel-release 源：yum install -y epel-release

   设置 nginx 安装源：vim /etc/yum.repos.d/nginx.repo

   【参考】<http://nginx.org/en/linux_packages.html>

   ```
   [nginx]
   name=nginx repo
   baseurl=http://nginx.org/packages/centos/7/$basearch/
   gpgcheck=0
   enabled=1
   ```

   安装：yum install -y nginx

   开机启动：systemctl enable nginx

3. 安装PHP

   设置源：rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm

   安装：

   ```shell
   yum -y install php72w php72w-cli php72w-fpm php72w-common php72w-devel php72w-embedded php72w-gd php72w-mbstring php72w-mysqlnd php72w-opcache php72w-pdo php72w-xml
   ```

4. 安装MySQL5.7

   下载源：wget -i -c http://dev.mysql.com/get/mysql57-community-release-el7-10.noarch.rpm

   安装：yum -y install mysql57-community-release-el7-10.noarch.rpm

   安装：yum -y install mysql-community-server

   启动：systemctl start mysqld.service

   【

   ​	可选操作：

   ​	修改密码时发现密码规则冲突，修改密码规则
   ​	set global validate_password_policy=0;
   ​	set global validate_password_length=1;（默认最低长度为 4）

    】

   修改密码：set password for root@localhost = password('123456');

   移除源：yum -y remove mysql57-community-release-el7-10.noarch