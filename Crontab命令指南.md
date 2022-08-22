### crontab命令理解

- 选择编辑器

  ````
  ranchoy@pc:~$ select-editor
  ````

- crond服务的启动与关闭

  - Centos系统

    ````
    # 查看状态
    service crond status
    # 启动
    service crond start
    # 关闭
    service crond restart
    ````

  - Ubuntu系统

    ````
    # 查看状态
    service cron status
    # 启动
    service cron stop
    # 关闭
    service cron restart
    ````

- crontab命令

  - 命令功能

    ````
    通过crontab 命令，我们可以在固定的间隔时间执行指定的系统指令或 shell script脚本。时间间隔的单位可以是分钟、小时、日、月、周及以上的任意组合。这个命令非常设合周期性的日志分析或数据备份等工作。
    ````

  - 命令格式

    ````
    crontab [-u user] file
    crontab [-u user] [ -e | -l | -r ]
    ````

  - 命令参数

    ````
    -u user：用来设定某个用户的crontab服务，例如，“-u ixdba”表示设定ixdba用户的crontab服务，此参数一般有root用户来运行；
    file：file是命令文件的名字,表示将file做为crontab的任务列表文件并载入crontab。如果在命令行中没有指定这个文件，crontab命令将接受标准输入（键盘）上键入的命令，并将它们载入crontab；
    -e：编辑某个用户的crontab文件内容。如果不指定用户，则表示编辑当前用户的crontab文件；
    -l：显示某个用户的crontab文件内容，如果不指定用户，则表示显示当前用户的crontab文件内容；
    -r：从/var/spool/cron目录中删除某个用户的crontab文件，如果不指定用户，则默认删除当前用户的crontab文件；
    -i：在删除用户的crontab文件时给确认提示。
    ````

  - 时间格式

    ````
    *表示任何时候都匹配
    "a,b,c" 表示a 或者 b 或者c 执行命令
    "a-b" 表示a到b 之间 执行命令
    "*/a" 表示每 a分钟(小时等) 执行一次
    ````

  - sh文件要引入环境变量

    ````
    #!/usr/bin/sh
    # 引入环境变量
    . ~/.profile # ubuntu
    . ~/.bash_profile # centos
    # 跳转至Scrapy项目目录
    cd /home/ranchoy/Desktop/ssr
    # 后台运行抓取
    scrapy crawl ssr
    ````

  - 部署sh脚本

    ````
    */1 * * * * sh /home/ssr/ssr.sh > /home/ssr.txt 2>&1
    ````

    