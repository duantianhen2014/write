## Nginx/Apache隐藏入口文件

#### 1. Nginx配置.conf文件

```
location / {
    root   /data/webroot/project/public/;
    try_files $uri $uri/ /index.php?$query_string;
    index index.php  index.html index.htm;
    if ( !-e $request_filename) {
        rewrite ^/(.*)$ /index.php/$1 last;
        break;
    }
}
```

#### 2. Apache配置.htaccess

```
<IfModule mod_rewrite.c>
  Options +FollowSymlinks -Multiviews
  RewriteEngine On

  RewriteCond %{REQUEST_FILENAME} !-d
  RewriteCond %{REQUEST_FILENAME} !-f
  RewriteRule ^(.*)$ index.php?/$1 [QSA,PT,L]
</IfModule>
```

