raspberrynote
=============
配置固定ip

1. 先把eth0相关的内容改为如下：
```
iface eth0 inet static
address 192.168.1.100 (此处 192.168.1.100为分配的固定ip)
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8
```
2. 重新启动网络
`sudo /etc/init.d/networking restart`
