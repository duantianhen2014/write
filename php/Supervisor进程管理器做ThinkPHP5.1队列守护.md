## Supervisor进程管理器做ThinkPHP5.1队列`守护`



PS: 配置示例

```shell
[program:supplier-worker]
process_name=%(program_name)s_%(process_num)02d
command=php /data/webroot/supplier/think --queue testQueue
autostart=true
autorestart=true
user=root
numprocs=2
redirect_stderr=true
stdout_logfile=/data/webroot/supplier/supplier-queue.log
```

