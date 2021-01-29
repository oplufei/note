# Git命令

## 项目（代码）从Github上clone到本地仓库

安装git

github添加ssh key

首次安装git配置账户信息

```c
git config --global user.name "yourname"
git config --global user.email "yourname@yourmail.com"
```

下载

```c
git clone git@github.com:oplufei/note.git
```

本地就有了note文件夹

## 本地仓库更新到Github

```c
git init					//初始化本地仓库
git status					//查看状态
git add --all				//将文件添加到本地仓库
git commit -m "首次提交"	 //提交到本地仓库
git remote add origin git@github.com:oplufei/note.git		//与Github上的分支建立链接
git pull --rebase origin main
git push -u origin main -f		//将刚刚提交的文件推送到Github上
```

