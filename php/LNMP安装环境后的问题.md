## LNMP安装环境后的问题

1. 打开站点500

   /usr/local/nginx/conf/fastcgi.conf 

   配置文件修改这行

   #fastcgi_param PHP_ADMIN_VALUE "open_basedir=$document_root/:/tmp/:/proc/";
   fastcgi_param PHP_ADMIN_VALUE "open_basedir=/home/wwwroot/:/tmp/:/proc/";

