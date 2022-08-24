### Docker使用指南

1. Docker基础命令

   - 容器运行

     ```
     $ docker run -it [docker-id] bash (运行一个指向docker-id的bash终端)
     $ docker exec -it [docker-id] bash (进入正在运行的docker-id的bash终端)
     ```

   - 容器管理

     ```
     $ docker info # docker的信息
     $ docker search [docker-name] # 查找远程的docker镜像
     $ docker rm [docker-name] # 删除容器
     ```

   - 镜像管理

     ```
     $ dokcer images [NULL|docker-name] # 查看本地镜像
     $ docker pull [image-name|image-name:version] # 下载镜像
     $ docker rmi [image-name] # 删除镜像
     $ docker image load -i [file-path] # 导入镜像
     $ docker image inspect [image-name] # 展示镜像详细信息 
     ```

   - 

2. 