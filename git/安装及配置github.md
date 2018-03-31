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

## 关联github提交代码
1. 在github中创建仓库

