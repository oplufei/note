# Git

[TOC]



## Git创建仓库

### 初始化

 使用当前目录作为Git仓库

```c
git init
```

使用指定目录作为Git仓库

```c
git init xxx 
```

当前目录下有几个文件想要纳入版本控制，需要先用 git add 命令告诉Git开始对这些文件进行跟踪，然后提交

```c
git add *.c
git add README
git commit -m '初始化项目版本'
```

以上命令将目录下以.c结尾及README文件提交到仓库中

### git clone

从现有Git仓库中拷贝项目

```c
git clone <repo>
```

克隆到指定目录

```c
git clone <repo> <directory>
```

#### 参数说明

- repo：Git仓库
- directory：本地目录

比如，要克隆Ruby语言的Git代码仓库Grit

```C
git clone git://github.com/schacon/grit.git
```

执行该命令后，会在当前目录下创建一个名为grit的目录，其中包含一个.git的目录，用于保存下载下来的所有版本记录

自己定义新建的项目目录名称

```C
git clone git://github.com/schacon/grit.git mygrit
```

### git config（配置）

显示当前的git配置信息

```C
git config --list
```

编辑git配置文件

```C
git config -e #针对当前仓库
```

或者：

```C
git config -e --global #针对系统上所有仓库
```

设置提交代码时的用户信息

```C
git config --global user.name"runoob"
git config --global user.email test@runoob.com
```

如果去掉--global参数，只对当前仓库有效

## Git基本操作

![](E:\2、IT\捕获.JPG)

### 说明：

- workspace：工作区
- staging area：缓存区/暂存区
- local repository：本地仓库
- remote repository：远程仓库

### 一个简单操作步骤：

```C
git init          
git add .
git commit
```

- 初始化仓库
- 添加文件到暂存区
- 将暂存区内容添加到仓库中

### 提交与修改

Git的工作就是创建和保存项目快照及与之后的快照进行对比

- git add：添加文件到仓库
- git status：查看仓库当前的状态，显示有变更的文件
- git diff：比较文件的不同，即暂存区和工作区的差异
- git commit：提交暂存区到本地仓库
- git reset：回退版本
- git rm：删除工作区文件
- git mv：移动或重命名工作区文件

### 提交日志

- git log：查看历史提交记录
- git blame <file>：以列表形式查看指定文件的历史修改记录

### 远程操作

- git remote：远程仓库操作
- git fetch：从远程获取代码库
- git pull：下载远程代码并合并
- git push：上传远程代码并合并

### 常用命令

1. git clone
2. git push
3. git add
4. git commit
5. git checkout
6. git pull

## Git分支管理

每一种版本控制系统都以某种形式支持分支。使用分支可以从开发主线分离，在不影响主线的同时继续工作

### 基本操作

创建分支

```C
git branch (branchname)
```

切换分支命令

```C
git checkout (branchname)
```

当切换分支的时候，Git会用该分支的最后提交的快照替换工作目录内容，多个分支不需要多个目录

合并分支命令

```C
git merge
```

可以多次合并到统一分支，也可以选择在合并之后直接删除被并入的分支

列出分支

```C
git branch
```

### 例子

1. #### 创建一个测试目录

   ```C
   mkdir gitdemo			//当前目录子目录
   cd gitdemo				//来到子目录
   git init				//初始化
   touch README			
   git add README
   git commit -m '第一次版本提交'
   ```

   %%%出现问题%%%

   ![](E:\2、IT\gitdemo\捕获.JPG)

   出现 >：因为commit的注释结构出错，如双引号缺失一半、右侧和左侧不一致等，git会误认为注释内容没有结束，于是会无限输出 >，直到获取到结尾的引号，此时git认为注释内容编辑结束，正常进入下一流程

   出现”untracked files“：Git中的分支，本质是指向commit对象的可变指针。Git会用master作为分支的默认名字。在若干次提交后，就有了一个指向最后一次提交对象的master分支，在每次提交的时候都会自动向前移动。

   ![](E:\2、IT\gitdemo\捕获3.JPG)

   用git add .添加之后，再提交就可以了

2. #### 初始状态及第一次新建分支

   ```c
   git init								//初始化默认创建master分支
   git branch (testing)					//新建testing分支
   ```

   ![](E:\2、IT\gitdemo\捕获4.JPG)

   当以此方式在上次提交更新之后创建了新分支，如果后来又有更新提交，然后又切换到了testing分支，Git将还原工作目录到创建分支时的样子

3. #### 切换分支

   