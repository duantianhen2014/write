## Nginx 跨域配置

直接上配置

```
server {
    listen       80;
    listen  [::]:80;
    server_name  localhost;
    client_max_body_size 256m;
    root /var/www/html/public;
    index index.php index.html index.htm;
    
    location = /50x.html {
        root   /usr/share/nginx/html;
    }

    location ~* .(jpg|gif|png|js|css)$ {
        root /var/www/html/public;
        if (-f $request_filename) {
        expires max;
            break;
        }
    }

    location ~* .*.(zip|docx|exe|xlsx|csv) {
        add_header  Content-Type    "application/octet-stream";
        if ( $args ~ ^filename=(.*) ) {
            add_header  Content-Disposition "attachment; filename=$1";
        }
    }
		#此处为跨域设置
    add_header 'Access-Control-Allow-Credentials' "true" always;
    add_header 'Access-Control-Allow-Origin' "$http_origin" always;
    add_header 'Access-Control-Allow-Methods' "GET,POST,PUT,DELETE,PATCH,OPTIONS" always;
    add_header 'Access-Control-Allow-Headers' "*" always;
    add_header 'Access-Control-Allow-Headers' "Origin,Access-Control-Allow-Headers,DNT,X-CustomHeader,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Authorization,Accept,Webtoken,Teamid" always;

    location / {
        client_max_body_size 256m;
        index index.php index.html index.htm;
				#此处为重点：跨域时浏览器会发送两条请求，第一个是options请求，返回这个header加状态码【状态码是重点】
        if ($request_method = 'OPTIONS') {
            add_header 'Access-Control-Allow-Origin' "$http_origin" always;
            add_header 'Access-Control-Allow-Credentials' 'true' always;
            add_header 'Access-Control-Allow-Headers' "Origin,Access-Control-Allow-Headers,DNT,X-CustomHeader,Keep-Alive,User-Agent,X-Requested-With,If-Modified-Since,Cache-Control,Content-Type,Authorization,Accept,Webtoken,Teamid" always;
            add_header 'Access-Control-Allow-Methods' 'GET,POST,PUT,DELETE,PATCH,OPTIONS';
            add_header 'Access-Control-Max-Age' 1728000;
            add_header 'Content-Type' 'text/plain; charset=utf-8';
            add_header 'Content-Length' 0;
            return 204;
        }

        if (!-e $request_filename) {
           rewrite  ^/(.*)$  /index.php/$1  last;
           break;
        }
    }

    location ~ ^(.+.php)(.*)$ {
        include fastcgi.conf;
        set $fastcgi_script_name2 $fastcgi_script_name;
        set $path_info $fastcgi_path_info;
        if ($fastcgi_script_name ~ "^(.+\.php)(/.+)$") {
            set $fastcgi_script_name2 $1;
            set $path_info $2;
        }
        fastcgi_param   PATH_INFO $path_info;
        fastcgi_param   SCRIPT_FILENAME   $document_root$fastcgi_script_name2;
        fastcgi_param   SCRIPT_NAME   $fastcgi_script_name2;
        fastcgi_pass  127.0.0.1:9000;
        fastcgi_index index.php;

    }
}
```

