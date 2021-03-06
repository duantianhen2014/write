## 整理Linux常用命令

转载 <https://shockerli.net/post/shell-practical-command-collection/>

> 本文档收集了常用的 Shell 命令组合，依然在不定期更新中…

## 终端命令

### 日志

#### 统计独立 IP 数量

| `1 ` | `awk '{print $1}' access.log | sort -n | uniq | wc -l` |
| ---- | ------------------------------------------------------ |
|      |                                                        |

#### 查看某一时间段的 IP 访问量

| `1 ` | `grep "05/Apr/2019:0[1-9]" access.log | awk '{print $1}' | sort | uniq -c| sort -nr | wc -l` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

#### 查看访问最频繁的前 100 个 IP

| `1 ` | `awk '{print $1}' access.log | sort -n | uniq -c | sort -rn | head -n 100` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

#### 查看访问 100 次以上的 IP

| `1 ` | `awk '{print $1}' access.log | sort -n | uniq -c | awk '{if($1 > 100) print $0}' | sort -rn` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

#### 查询某个 IP 的详细访问情况，按访问频率排序

| `1 ` | `grep '127.0.0.1' access.log | awk '{print $7}' | sort | uniq -c | sort -rn | head -n 100` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

#### 统计 URL 访问量排行

| `1 ` | `awk '{url[$7]++} END {for (k in url) {print url[k],k}}' nginx.access.log | sort -rn` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

使用 `awk` 从 Nginx 日志中逐行统计 URL 访问计数，然后使用 `sort` 对结果进行排名

#### 访问最频繁的 URL

| `1 ` | `awk '{print $7}' access.log | sort | uniq -c | sort -rn | head -n 100` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

或者

| `1 ` | `awk '{url[$7]++} END {for (k in url) {print url[k],k}}' access.log | sort -rn | head -n 100` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

#### 除了 .php 以外，访问最频繁的 URL

| `1 ` | `grep -v ".php" access.log | awk '{print $7}' | sort | uniq -c | sort -rn | head -n 100` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

#### URL 访问次数超过 100 次的页面

| `1 ` | `awk '{print $7}' access.log | sort -n | uniq -c | sort -rn | head -n 100` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

#### 查看最近1000条记录，访问量最高的 URL

| `1 ` | `tail -1000 access.log | awk '{print $7}' | sort | uniq -c | sort -rn | less` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

#### 统计每秒的请求数，TOP100的时间点(精确到秒)

| `1 ` | `awk '{print $4}' access.log | cut -c 14-21 | sort | uniq -c | sort -rn | head -n 100` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

#### 统计每小时的请求数，TOP100的时间点(精确到小时)

| `1 ` | `awk '{print $4}' access.log | cut -c 14-15 | sort | uniq -c | sort -rn | head -n 100` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

#### 列出传输时间超过3秒的页面，并统计其出现的次数，显示前20条

> 在 Nginx log 最后一个字段加入 `$request_time`

| `1 ` | `cat access.log | awk '($NF > 3){print $7}' | sort -n | uniq -c | sort -rn | head -20` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

#### 列出PHP页面请求时间超过3秒的页面，并统计其出现的次数，显示前100条

> 在 Nginx log 最后一个字段加入 `$request_time`

| `1 ` | `cat access.log | awk '($NF > 1 && $7~/\.php/){print $7}' | sort -n | uniq -c | sort -rn | head -100` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

### 文件

#### 列出当前目录下的所有文件（包括隐藏文件）的绝对路径

| `1 ` | `find $PWD -maxdepth 1 | xargs ls -ld` |
| ---- | -------------------------------------- |
|      |                                        |

#### 递归列出当前目录下的所有文件（包括隐藏文件）的绝对路径

| `1 ` | `find $PWD | xargs ls -ld` |
| ---- | -------------------------- |
|      |                            |

#### 在每行记录的开头加上当前路径

| `1 ` | `ls | sed "s:^:`pwd`/:"` |
| ---- | ------------------------ |
|      |                          |

#### 删除指定时间之前的文件

| `1 ` | `find /path/to/dir -mtime +30 -type f | xargs rm -f` |
| ---- | ---------------------------------------------------- |
|      |                                                      |

- `/path/to/dir` 设置查找的目录
- `--mtime +30` 设置时间为30天前
- `-type f` 指定查找的类型为文件

#### 删除文件前/后N行

删除了前2行。先用`tail`把从第3行开始的所有内容输出到新文件，然后再重命名文件。

| `1 2 ` | `tail -n +3 old_file > new_file  mv new_file old_file` |
| ------ | ------------------------------------------------------ |
|        |                                                        |

仅保留最后3行。

| `1 2 ` | `tail -n -3 old_file > new_file  mv new_file old_file` |
| ------ | ------------------------------------------------------ |
|        |                                                        |

如果写定时任务，那可放置到一行。

| `1 ` | `0 0 * * * tail -n -3 old_file > new_file && mv -f new_file old_file` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

### 网络

#### 统计网卡的流量数据

| `1 2 3 4 5 ` | `sar -n DEV 1 5      平均时间:     IFACE   rxpck/s   txpck/s    rxkB/s    txkB/s   rxcmp/s   txcmp/s  rxmcst/s 平均时间:        lo      2.21      2.21      0.18      0.18      0.00      0.00      0.00 平均时间:      eth0      4.62      3.82      0.37      1.90      0.00      0.00      0.00` |
| ------------ | ------------------------------------------------------------ |
|              |                                                              |

命令中 1 5 表示每一秒钟取 1 次值，一共取 5 次。

命令执行后会列出每个网卡这 5 次取值的平均数据，根据实际情况来确定带宽跑满的网卡名称，默认情况下 eth0 为内网网卡，eth1 为外网网卡。

#### 查询占用端口的进程/程序

| `1 2 3 ` | `netstat -tunlp | grep ':80'      tcp        0      0 0.0.0.0:80      0.0.0.0:*    LISTEN      26655/nginx` |
| -------- | ------------------------------------------------------------ |
|          |                                                              |

或者使用 `lsof` 命令：

| `1 ` | `lsof -i :80` |
| ---- | ------------- |
|      |               |

#### 查看流量占用情况

| `1 ` | `iftop -P` |
| ---- | ---------- |
|      |            |

#### 查看程序流量排行

| `1 ` | `nethogs` |
| ---- | --------- |
|      |           |

### 进程/程序

#### grep 程序并杀死

| `1 ` | `ps -ef | grep process_name | grep -v grep | cut -c 9-15 | xargs kill -s 9` |
| ---- | ------------------------------------------------------------ |
|      |                                                              |

#### 查看指定进程的具体占用内存

| `1 ` | `cat /proc/[pid]/status` |
| ---- | ------------------------ |
|      |                          |

| ` 1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19 20 21 22 23 24 ` | `Name:	memcached State:	S (sleeping) Tgid:	1954 Pid:	1954 PPid:	1 TracerPid:	0 Uid:	500	500	500	500 Gid:	500	500	500	500 Utrace:	0 FDSize:	128 Groups: VmPeak:	  413792 kB VmSize:	  360544 kB VmLck:	       0 kB VmHWM:	   29704 kB VmRSS:	   29376 kB VmData:	  341768 kB VmStk:	    2132 kB VmExe:	      80 kB VmLib:	    2152 kB VmPTE:	     164 kB VmSwap:	       0 kB Threads:	6 ...` |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
|                                                              |                                                              |

其中，`VmRSS`项表示实际占用内存值。

或者，用`ps`命令

| `1 ` | `ps aux | grep <pid>` |
| ---- | --------------------- |
|      |                       |

| `1 2 ` | `USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND jxcdn     1954  0.0  0.1 360544 29376 ?        Ssl  Apr13   7:56 memcached -m 128 -p 11211` |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

其中`RSS`列表示实际使用内存(单位: KB)。可以看出，与`/proc/[pid]/status`的值是一致的。

## 脚本命令

#### 获取脚本文件所在目录

| `1 ` | `script_path=$(cd `dirname $0`; pwd)` |
| ---- | ------------------------------------- |
|      |                                       |

#### 获取脚本文件的上级目录

| `1 2 ` | `script_path=$(cd `dirname $0`; pwd) root_path=$(cd `dirname "$script_path"`; pwd)` |
| ------ | ------------------------------------------------------------ |
|        |                                                              |

#### 格式化当前时间

| `1 ` | `datetime=$(date +"%Y-%m-%d %H:%M:%S")` |
| ---- | --------------------------------------- |
|      |                                         |

#### 去除文本中的颜色转义符

| `1 ` | `sed -r "s/\x1B\[([0-9]{1,2}(;[0-9]{1,2})?)?[m|K]//g"` |
| ---- | ------------------------------------------------------ |
|      |                                                        |