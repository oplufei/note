# Git命令

## 项目（代码）从Github上clone到本地仓库

### 安装git

### github添加ssh key

```c
ssh-keygen -t rsa -C "youremail@example.com"		//生成SSH KEY
```

默认生成在C:\Users\Administrator\.ssh

打开 **id_rsa.pub**，复制里面的 key

回到 github 上，进入 Account => Settings（账户配置）

左边选择 **SSH and GPG keys**，然后点击 **New SSH key** 按钮,title 设置标题，可以随便填，粘贴在你电脑上生成的 key。

为了验证是否成功，输入以下命令：

```
ssh -T git@github.com
```

首次安装git配置账户信息

```c
git config --global user.name "yourname"
git config --global user.email "yourname@yourmail.com"
```

### 下载

```c
git clone git@github.com:oplufei/note.git
```

ssh地址，未配置ssh key会出现

```
$ git clone git@github.com:oplufei/note.git
Cloning into 'note'...
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.
```

或者

```c
git clone https://github.com/oplufei/note.git
```

本地就有了note文件夹

## 本地仓库更新到Github

网上找到的命令

```c
git init					//初始化本地仓库
git status					//查看状态
git add --all				//将文件添加到本地仓库
git commit -m "首次提交"	 //提交到本地仓库
git remote add origin git@github.com:oplufei/note.git		//与Github上的分支建立链接
git pull --rebase origin main
git push -u origin main -f		//将刚刚提交的文件推送到Github上
```

今天成功操作的

```c
git init
git add Git命令.md
git commit -m "家台式机更新Git命令"
git push -u origin main -f
```

没有绑定ssh的时候，每次提交都要输入用户名密码

更新所有

```
git add .
git commit -m '更新文件夹内所有内容'
git push
```

更新文件夹（只有一个文件夹）

```
git add 文件夹名
git commit
git push
```

## 分支

### 更改默认分支名称

```
git branch -m main master					#重命名
git fetch origin
git branch -u origin/master master
```

### 新建分支

```
git branch 新建的分支名字
```

### 删除本地分支

先切换到要删除的分支再删除当前分支

```
git checkout main
git branch -d main
```

强制删除

```
git branch -D main
```

### 删除远程分支

```
git push origin --delete main
```

## 解决github网页打不开的方法

### 一、hosts文件究竟起到什么作用呢？

经常在网上看到修改hosts文件，那hosts文件究竟起到什么作用呢？
  很简单, 因为无论你上网打的什么网站地址, 实际上最终总归是要转换成一个IP地址才能访问的,平时这个转换工作是有网络上的DNS服务器来完成的. 但是有些时候,有些网站, 由于某些原因,网络上的DNS服务器无法给出正确的或可用IP地址(天朝特别多, 大家懂的),   这个时候hosts文件就可以代劳了,你可以直接用记事本打开这文件看看就知道了, 里面一行就是一条记录, 一个IP地址接一个空格或tab, 再后面就是一个网址.
  它起到的作用就是直接在你本机上就把这些网址翻译成IP地址.
  本地预先配置的DNS数据，解析域名的时候首先试图从hosts文件获取，没有则从DNS服务器获取。

此文件的三个主要用途：
  1，配置没有在DNS注册的域名，这对于局域网的服务有一定的价值，这是正常使用目的
  2，避开DNS服务实现某域名指向正确地址，防止别有用心的DNS误导
  3，避开DNS服务实现某域名指向错误地址，防止讨厌的广告

补充一点背景资料：
从Windows 2000开始，Windows解析名称的顺序为： DNS cache --> hosts 文件 -->DNS Server –> NetBIOS cache --> WINS Server --> 广播 --> LMHOSTS 文件
hosts 文件的优先级高于 DNS Server，因此修改hosts文件可以跳过被污染的dns服务器。
更规范的做法是修改hosts之后，使用 ipconfig /flushdns 来清空DNS cache.

### 二、具体操作

#### 2.1 进入下面两个网址，提取ip地址

https://github.com.ipaddress.com/
https://fastly.net.ipaddress.com/github.global.ssl.fastly.net

#### 2.2 前往文件夹 C:\Windows\System32\drivers\etc

寻找hosts文件，你需要将其移出来操作，若是你在原地操作的话，会提示你没有权限的，建议移到桌面，然后以txt方式打开编辑，保存，最后将文件放回原来的目录下。

在文件末尾添加如下内容 ，根据自己所得到的 ip地址进行修改。

打开命令端口键盘最下面一行左边第二个 + R打开，输入cmd确认，输入ipconfig/fiushdns

————————————————
版权声明：本文为CSDN博主「&amp;~&amp;」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/LJP1924804579/article/details/107894684