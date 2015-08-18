# Docker镜像

### 拉取镜像
`docker pull`

### 查看镜像的构建历史
`docker history [image-name]`。可根据历史，run对应阶段的镜像来debug。

## 使用Dockerfile创建镜像
官方手册：[Dockerfile reference](https://docs.docker.com/reference/builder/)。

### 指令

#### CMD
指定容器被启动时要运行的命令。

#### ENTRYPOINT
容器被启动时要运行的命令。不同于CMD的是，命令默认不能被覆盖。可与CMD配合，设置默认命令。

#### WORKDIR
设置容器内的工作目录。

#### ENV
设置环境变量。

#### USER
指定运行身份。默认为root。

#### VOLUME
向容器添加卷。

#### ADD
向容器添加文件。

#### COPY
类似于ADD。但：

* 不会自动提取和解压
* 文件必须在构建目录内（Dockerfile同一目录）
* 复制在docker守护进程中进行

#### ONBUILD
添加触发器，使对应命令在子镜像构建的时候运行。
