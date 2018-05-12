## 介绍
Docker是一个开源的容器引擎，它有助于更快地交付产品。Docker可将应用程序和基础设施层隔离，并且将基础设施当作程序一样进行管理。使用Docker，可以更快地打包，测试以及部署应用程序，并可以缩短从编程到部署运行代码的周期。

## Docker架构
### 1. Docker daemon
守护进程，运行在宿主机（DOCKER_HOST）的后台进程，可通过Docker客户端与之通信
### 2. Client
Docker客户端时Docker的用户界面，可以接受用户命令和配置标识，并且Docker daemon通信
### 3. Images
Docker镜像是一个只读模板，包含创建Docker容器的说明。Docker镜像可以运行Docker镜像中的程序
### 4. Container 
容器是镜像的可运行实例。镜像与容器类似与面向对象中类与对象的关系。可通过Docker API或者CLI命令起停，移动，删除等。
### 5.Register 
Docker Register是一个集中存储与分发镜像的服务。构建完Docker镜像后，就可在当前宿主机上运行。但如果想在其他机器上运行这个镜像，就需要手动复制。此时可以借助Docker Register避免复制。
一个Docker Register可以包含多个Docker仓库，每个仓库可包含多个镜像标签，每个标签对应一个Docker镜像。

## 系统要求
>必须是 64 位操作系统,  
建议内核在 3.8 以上
centos、Ubuntu操作系统
