# Docker：容器

### 添加

```bash
# 例子
docker run -i -t ubuntu /bin/bash
```

`run`命令通过镜像开启一个新的容器。参考手册：[Docker run reference](https://docs.docker.com/reference/run/)。

* `-d`：守护运行
* `-v`：挂载
* `--rm`：容器退出后自动清理数据
* `--name`：为容器添加名字
* `-w`：WORKDIR

#### 创建守护式容器（daemonized container）
开启容器的时候使用`-d`参数。

### 修改

对容器的修改可能包括：
* 停止运行：容器的命令执行完后会自动停止；而对于使用`-d`在后台运行的容器，可以用'docker stop'来停止
* 重新启动：`docker start`
* 附着到容器上：`docker attach`
* 在容器内执行命令： `docker exec`

#### exec
`docker exec -it [container-id] bash`，对容器开启一个新的bash。

### 查看（容器相关信息）

#### 查看容器日志
容器内的stdout和stderr都会写进容器日志里。`logs`命令可以查看容器日志：`docker logs [container-name]`

#### 查看容器内的进程
使用`docker top [container-name]`。

#### 查看容器详细信息
使用`docker inspect`。

### 删除
`docker rm`。

## 连接容器
[Linking containers together](https://docs.docker.com/userguide/dockerlinks/)

## 实战：

### 容器自动重启
`docker run --restart=always`

### 删除全部容器
```
docker rm `docker ps -aq`
```
