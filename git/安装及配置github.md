## git结合github安装：
[git安装](https://blog.csdn.net/dietime1943/article/details/71751007)  
[配置github](https://blog.csdn.net/angus_monroe/article/details/78543289)

1. 制定用户名和邮箱：  
git config --global user.name "wang.kaixiang"  
git config --global user.email "wangkx2010@foxmail.com"

2. 设置大小写敏感  
git config core.ignorecase false

3. 生成密钥：ssh-keygen -t rsa -C "wangkx2010@foxmail.com"

4. 添加你的 SSH key 到 github上面去  
a.拷贝 id_rsa.pub 文件的内容  
b. 登录你的github账号，从又上角的设置（ Settings ）进入，
然后点击菜单栏的 SSH and GPG keys 进入页面添加 SSH key。    
c. 点击 Add SSH key 按钮添加一个 SSH key 。
把你复制的 SSH key 代码粘贴到 key 所对应的输入框中，
记得 SSH key 代码的前后不要留有空格或者回车。当然，
上面的 Title 所对应的输入框你也可以输入一个该 SSH key
显示在 github 上的一个别名。默认的会使用你的邮件名称。

## TortoiseGit
### 密钥配置
TortoiseGit 使用扩展名为ppk的密钥，而不是ssh-keygen生成的rsa密钥。使用命令ssh-keygen -C "邮箱地址" -t rsa产生的密钥在TortoiseGit中不能用。而基于git的开发必须要用到rsa密钥，因此需要用到TortoiseGit的putty key generator工具来生成既适用于git的rsa密钥也适用于TortoiseGit的ppk密钥。打开putty自动生产ppk密钥工具，将ssh中之前生产的密钥导入进来，然后利用Pageant保存增加进来即可。  
![](http://imglf6.nosdn.127.net/img/Z3JBcDVLWHRpSFZvcGc1OUUrckdaS2o0Y1Z1ZWlvb1ozU3R1M05JZDlNMzBoSlkzM2FINjdBPT0.png?imageView&thumbnail=500x0&quality=96&stripmeta=0)  



[参考](https://blog.csdn.net/bendanbaichi1989/article/details/17916795)
###   状态图标不能正常显示
1. 修改注册表
2. 在TortoiseGit 重新设置setting中的Icon Overlays/Icon Set,亲测可用

## 关联github提交代码
1. 在github中创建仓库
2. 在个github中复制clone命令，克隆代码到本地
3. 本地提交修改即可

## 本地代码与github关联
1. git init  初始化，生产.git文件
2. 正常add、commit提交
3. 生成远端库：git remote add origin https://github.com/melody2017/melody-dubbo-parent.git
4. 正常推送代码：git push -u origin master 

