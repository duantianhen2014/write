## Nginx知识点

```nginx
location ~* \.(config|ini|docx|txt|doc)$ {
          # deny all;
                return 404;
}
```

