资料：

[官方文档：Gunicorn - Python WSGI HTTP Server for UNIX](https://gunicorn.org/)

[官方文档配置说明：Settings — Gunicorn 20.1.0 documentation](https://docs.gunicorn.org/en/latest/settings.html#settings)

[一文详解gunicorn的功能及使用方法](https://blog.csdn.net/xu710263124/article/details/118975404)





## 启动参数

```shell
gunicorn -c gunicorn_config.py test:app
```



> 1)-c CONFIG,–config=CONFIG
> 指定一个配置文件（py文件）
> 2)-b BIND,–bind=BIND
> 与指定socket进行绑定
> 3)-D,–daemon
> 后台进程方式运行gunicorn进程
> 4)-w WORKERS,–workers=WORKERS
> 工作进程的数量
> 5)-k WORKERCLASS,–worker-class=WORKERCLASS
> 工作进程类型，包括sync（默认）,eventlet,gevent,tornado,gthread,gaiohttp
> 6)–backlog INT
> 最大挂起的连接数
> 7)–log-level LEVEL
> 日志输出等级
> 8)–access-logfile FILE
> 访问日志输出文件
> 9)–error-logfile FILE
> 错误日志输出文件

### Gunicorn配置文件

```python
# gunicorn.conf
# coding:utf-8
import multiprocessing
# 并行工作进程数, int，cpu数量*2+1 推荐进程数
workers = multiprocessing.cpu_count() * 2 + 1  
# 指定每个进程开启的线程数
threads = 3 
# 绑定的ip与端口
bind = '0.0.0.0:5000' 
# 设置守护进程,将进程交给supervisor管理
daemon = 'false'
# 工作模式协程，默认的是sync模式
worker_class = 'gevent'
# 设置最大并发量（每个worker处理请求的工作线程数，正整数，默认为1）
worker_connections = 2000
# 
max_requests = 2000
# 设置进程文件目录
pidfile = '/home/your_path/gunicorn.pid'
# 设置访问日志和错误信息日志路径
accesslog = '/home/your_path/gunicorn_acess.log'
errorlog = '/home/your_path/gunicorn_error.log'
# 日志级别，这个日志级别指的是错误日志的级别，而访问日志的级别无法设置
loglevel = 'info' 
# 设置gunicorn访问日志格式，错误日志无法设置
access_log_format = '%(t)s %(p)s %(h)s "%(r)s" %(s)s %(L)s %(b)s %(f)s" "%(a)s"'
# 监听队列
backlog = 512                
#进程名
proc_name = 'gunicorn_process'   
# 设置超时时间120s，默认为30s。按自己的需求进行设置timeout = 120
timeout = 120      
# 超时重启
graceful_timeout = 300
# 在keep-alive连接上等待请求的秒数，默认情况下值为2。一般设定在1~5秒之间。
keepalive = 3
# HTTP请求行的最大大小，此参数用于限制HTTP请求行的允许大小，默认情况下，这个值为4094。
# 值是0~8190的数字。此参数可以防止任何DDOS攻击
limit_request_line = 5120
# 限制HTTP请求中请求头字段的数量。
#  此字段用于限制请求头字段的数量以防止DDOS攻击，与limit-request-field-size一起使用可以提高安全性。
# 默认情况下，这个值为100，这个值不能超过32768
limit_request_fields = 101
# 限制HTTP请求中请求头的大小，默认情况下这个值为8190。
# 值是一个整数或者0，当该值为0时，表示将对请求头大小不做限制
limit_request_field_size = 8190
# 设置gunicorn使用的python虚拟环境
pythonpath='/home/your_path/venv/bin/python3'
# 环境变量
raw_env = 'APE_API_ENV=DEV'
```



说明

## max_requests

命令行`--max-requests INT` 默认值是0 该参数的含义是：在重启之前工作进程（worker）能处理的最大请求数，任何一个大于0的值都会限制工作进程（worker）在重启之前处理的请求数量，这是一种帮助限制内存泄漏的简单方法。 如果该值设置为0（默认值）那么工作进程的自动重启是被禁用

## timeout

命令行-t INT 或者--timeout INT 默认值是30秒。 工作进程在超过设置的超时时间内没有响应将会被杀死并重启。 当值为0就表示禁用超时设置。 通常，默认的30秒就够了，只有当确定对同步工作进程有影响时才会修改该值。对于非同步工作进程，这意味着工作进程仍在运行，不受处理单个请求所需的时间的限制。

## keepalive

命令行--keep-alive INT 默认值是2 连接超时时间，通常设置在1-5秒范围内。