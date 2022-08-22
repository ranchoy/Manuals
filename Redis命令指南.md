### Redis命令行操作

- 编辑redis.conf配置文件

  ````
  ranchoy@pc:~$ sudo gedit /etc/redis/redis.conf
  ````

- 基础命令

  ````
  1.启动：
  ranchoy@pc:~$ /etc/init.d/redis-server start
  2.停止：
  ranchoy@pc:~$ /etc/init.d/redis-server stop
  3.重启：
  ranchoy@pc:~$ /etc/init.d/redis-server restart
  ````

- 查看Redis主从服务器信息

  ````
  ranchoy@pc:~$ redis-cli
  127.0.0.1:6379> info replication
  ````

- Redis文件所在位置

  ````
  1.日志文件所在位置：/var/log/redis/redis-server.log
  2.redis安装目录：/var/lib/redis（命令是：config get dir）
  ````

  