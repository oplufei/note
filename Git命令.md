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

