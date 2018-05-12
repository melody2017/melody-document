[安装指导](http://www.jb51.net/article/100455.htm)
## 在ubuntu14.04上安装Docker
运行命令：uname -a  
查看系统位数，
cat /etc/lsb-release

1. Docker安装命令： 
``` 
sudo apt-get update  
sudo apt-get install docker.io
```


2. 检查docker是否安装成功  
```
docker version
```
如果不是root用户的的操作，可以添加一个用户到Docker用户组，这样操作Docker时无需使用sudo命令
sudo gpasswd -a USER docker

3. 创建软连接
```
ln -sf /usr/bin/docker.io /usr/local/bin/docker
sed -i '$acomplete -F _docker docker' /etc/bash_completion.d/docker.io
```
4. 检查dockers服务
```
service docker status
service docker stop
service docker start
```
要把Docker以守护进程的方式运行，执行以下命令：（注意需先关闭Docker服务）
```
docker -d &
```
5. 设置docker自启动
```
pdate-rc.d docker defaults
```

6. 卸载Docker  
```
sudo docker -v  
sudo apt-get remove docker  
sudo apt-get remove --auto-remove docker  
sudo apt-get remove --purge lxc-docker  (这里的lxc-docker不是固定的也可以是docker.io)  
sudo apt-get autoremove --purge 
```
刚安装后卸载可能不会成功，可能是因为刚安装完软件，软件源还来不及更新，所以才会无法找到包。可以先使用apt-get update

7. Ubuntu下docker使用非root权限运行docker
默认情况下，docker 命令会使用 Unix socket 与 Docker 引擎通讯。而只有 root 用户和 docker 组的用户才可以访问 Docker 引擎的 Unix socket。出于安全考虑，一般 Linux 系统上不会直接使用 root 用户。因此，更好地做法是将需要使用 docker 的用户加入 docker 用户组。
  1. 添加 docker group ：
  ```
  sudo groupadd docker
  ```
  2. 将用户加入该 group 内
  ```
  $ sudo usermod -aG docker $USER
# 或者使用下面命令
$ sudo gpasswd -a ${USER} docker
  ```
  3. 重启服务
  ```
  $ sudo service docker restart
# 或者
$ sudo /etc/init.d/docker restart
  ```

8. Docker中配置国内镜像  
  1. 为什么要为docker配置国内镜像  
  在正常情况下，docker有一个默认连接的国外官方镜像，在国外的网友访问该官方镜像自然不成问题，
  但是国内毕竟不是国外，由于国情不同，中国的网络访问国外官方镜像网速一向很慢，而且往往还会遭遇断网的窘境，所以说我们要想正常使用docker的镜像，那么我们就不得不配置相应的国内镜像

  2. 可以使用的国内镜像有哪些
  阿里云，网易蜂巢，DaoCloud，Docker中国区官方镜像
  
  3. 配置Docker中国区官方镜像  
  在国内，可以通过registry.docker-cn.com访问官方镜像库，目前该镜像库只包含流行的公有镜像，而私有镜像仍需要从美国镜像库中拉取。
  
  4. 配置Docker中国区官方镜像  
  使用vi修改 /etc/docker/daemon.json 文件并添加上”registry-mirrors”: [“https://registry.docker-cn.com“]，如下：
  ```
  vi /etc/docker/daemon.json 
{ "registry-mirrors": ["https://registry.docker-cn.com"] }
  ```
  5. 重启Docker,使配置文件生效
  ```
  systemctl daemon-reload 
systemctl restart docker
```
[配置阿里云镜像仓库](https://jingyan.baidu.com/album/f3e34a12c607f4f5eb653596.html?picindex=5)

https://17pk264r.mirror.aliyuncs.com
## FAQ
### Docker的Ubuntu镜像安装的容器无ifconfig命令和ping命令
安装：
```
apt-get update
apt install net-tools       # ifconfig 
apt install iputils-ping     # ping
```




