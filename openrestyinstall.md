#树莓派安装OpenResty服务

##编译
```
$ ssh pi@raspberrypi.local
$ sudo apt-get update
$ sudo apt-get install libreadline-dev libpcre3-dev libssl-dev perl libncurses5-dev
$ wget http://openresty.org/download/ngx_openresty-1.4.1.1.tar.gz
$ tar xzvf ngx_openresty-1.4.1.1.tar.gz
$ cd ngx_openresty-1.4.1.1
$ ./configure --with-luajit
$ make
$ make install
```

##创建工作目录
```
$ mkdir work
$ cd work
$ mkdir logs/ conf/
```

##Config file
```
worker_processes  1;
error_log logs/error.log;
events {
        worker_connections 1024;
}
http {
    server {
        listen 8080;
        location / {
            default_type text/html;
            content_by_lua '
                ngx.say("<p>hello, world</p>")
            ';
        }
    }
}
```

##环境配置

```
$ PATH=/usr/local/openresty/nginx/sbin:$PATH
$ export PATH
$ nginx -p `pwd`/ -c conf/nginx.conf
```
