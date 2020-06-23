## laragon中ThinkPHP的nginx配置

以下这段为后添加

    location / {
    	if (!-e $request_filename) {
           rewrite  ^(.*)$  /index.php?s=$1  last;
    	   break;
         }
        try_files $uri $uri/ /index.php$is_args$args;
    	autoindex on;
    }
```nginx

server {
    listen 80;
    server_name tp5.test *.tp5.test;
    root "D:/laragon/www/tp5/public/";
    
    index index.html index.htm index.php;
 
    location / {
		if (!-e $request_filename) {
           rewrite  ^(.*)$  /index.php?s=$1  last;
		   break;
         }
        try_files $uri $uri/ /index.php$is_args$args;
		autoindex on;
    }
    
    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass php_upstream;		
        #fastcgi_pass unix:/run/php/php7.0-fpm.sock;
    }
	
	
    charset utf-8;
	
    location = /favicon.ico { access_log off; log_not_found off; }
    location = /robots.txt  { access_log off; log_not_found off; }
    location ~ /\.ht {
        deny all;
    }
}
# This file is auto-generated.
# If you want Laragon to respect your changes, just remove the [auto.] prefix

```

