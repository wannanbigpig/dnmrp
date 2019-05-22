# dnmrp
docker + nginx + mysql + redis + php

### 安装
1、拉取仓库代码到本地
```bash
git clone ...
cd dnmrp # 进入项目目录
```
2、执行docker-compose命令
```bash
docker-compose up
```
> 等待构建完成浏览器输入`localhost:8080`进入`phpmyadmin`系统可以查看`mysql`，
`8081`端口进入`phpredisadmin`,`80`端口可以查看`PHP`信息


### 说明
> PHP的构建已经完成，扩展等和dockerfile中一样，并且上传到docker-hub        
> 有特殊需求的话可以自行修改dockerfile，并且修改docker-compsoe.yml中注释部分，使用dockerfile构建        
> file/ext目录下存放PHP扩展文件，可以去pecl下载
