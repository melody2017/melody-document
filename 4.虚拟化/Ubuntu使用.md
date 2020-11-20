# ubuntu使用介绍
------

## 1. 操作命令
```
1. 查看ssh服务是否启动： ps -ef | grep sshd  或者 /etc/init.d/ssh status
```

## 2. 操作
### 1. 如何开启终端
快捷键：ctrl+alt+t
### 2. 修改静态IP
```
1. /etc/network/interfaces
auto lo
iface lo inet loopback
 
auto eth0
iface eth0 inet static *******定义为静态IP
 
address 192.168.1.168  *******所要设置的IP地址
netmask 255.255.255.0 *******子网掩码
gateway 192.168.0.1  *******网关（路由地址）
dns-nameserver 192.168.1.1     ****可以通过windows上查看后配置
```

2. 手动设置DNS服务器
```
打开文件/etc/resolv.conf，设置内容如下
nameserver 192.168.2.1 ******网关（同上）
nameserver 202.106.0.20 ******DNS服务器地址（我是参照其他电脑链接到此网络上查到的）
```
3. 重启Ubuntu后发现不能上网，问题出现在/etc/resolv.conf。
重启后，此文件配置的dns又被自动修改为默认值。所以需要永久性修改DNS。
方法为:打开文件/etc/resolvconf/resolv.conf.d/base，写入一下内容：
nameserver 192.168.2.1
nameserver 202.106.0.20

4. 重启networking服务，使其生效，命令为：/etc/init.d/networking restart

### 安装软件
1. ssh安装：apt-get install ssh



