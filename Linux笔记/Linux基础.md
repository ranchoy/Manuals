## Linux基础

1. 日志管理

   各类型日志目录介绍

   ```
   /var/log/messages：常规日志消息
   /var/log/messages：常规日志消息
   /var/log/boot：系统启动日志
   /var/log/debug：调试日志消息
   /var/log/auth.log：用户登录和身份验证日志
   /var/log/daemon.log：运行squid，ntpd等其他日志消息到这个文件
   /var/log/dmesg：Linux内核环缓存日志
   /var/log/dpkg.log：所有二进制包日志都包括程序包安装和其他信息
   /var/log/faillog：用户登录日志文件失败
   /var/log/kern.log：内核日志文件
   /var/log/lpr.log：打印机日志文件
   /var/log/mail.*：所有邮件服务器消息日志文件
   /var/log/mysql.*：MySQL服务器日志文件
   /var/log/user.log：所有用户级日志
   /var/log/xorg.0.log：X.org日志文件
   /var/log/apache2/*：Apache Web服务器日志文件目录
   /var/log/lighttpd/*：Lighttpd Web服务器日志文件目录
   /var/log/fsck/*：fsck命令日志
   /var/log/apport.log：应用程序崩溃报告/日志文件
   /var/log/syslog：系统日志
   /var/log/ufw：ufw防火墙日志
   /var/log/gufw：gufw防火墙日志
   ```

   

2. 进程管理