---
title: git的使用方法与概念理解（上）
date: 2024-11-05 11:13:32
categories: 技术
tags:
  - git
  - 技术
---

# git笔记（上）

git官网安装

右键->more->在终端中打开&Git Bash Here

win+R然后cmd进入终端

or在对应文件资源管理器下cmd进入终端or右键

or  vscode中打开终端

## git的使用方式

- **命令行**
- 图形化界面（GUI）
- IDE插件、扩展



>为了区分Linux操作系统中的命令，Git命令行均已git开头，后跟一个具体的命令

![72742884470](C:\Users\13518\AppData\Local\Temp\1727428844702.png)

**看到版本信息：**

git-v

**美化终端：**

Windows：posh-Git

###设置姓名邮箱：

git config --global user.name "na me"（有空格就用引号，无空格不需要）

git config --global global user.email 具体邮箱

git config --global credential.helper store保存用户名和密码（不用每次输入了）

git config --global --list查看git配置信息

![72743574318](C:\Users\13518\AppData\Local\Temp\1727435743185.png)

###创建仓库：

**法一：电脑本地创建仓库**

**git  init初始化仓库**

```
git learn-git(创建母录mkdir（make  directories）)
cd learn-git(切换目录cd(change directory))
git init(创建仓库)
```

**看看git被隐藏的part（勿删改）:**git bash（windows）

**具体目录**

```
git init +指定项目的名称（生成git仓库的目录不同）
```

**法二：从远程服务器上克隆一个已经存在的仓库**

git clone +url

**清空仓库：**

\rm -rf  .git



#### 补充内容

```
补充知识点
-命令行指令ls, 列出目录(文件夹)下文件, ls for list
-l, 以每行一个的格式列出文件, l for long
-a, 列出包含隐藏文件的所有文件, a for all
-S, 以文件大小顺序列出文件, S for Size
-t, 以修改日期顺序列出文件, t for time modified
-r, 以倒序列出文件，r for reverse
参数可以叠加，ls-ltr就是每行一条以文件修改日期倒序排列列出文件
-命令行指令mkdir, 新建目录(文件夹), Make Directory
-命令行指令cd, 切换目录(文件夹), Change Directory
cd ~ 跳到自己的home目录(文件夹)
cd../.. 跳到目前目录的上上两层
-命令行指令rm 用于删除文件、目录, rm for remove
-i 删除前提示, y删除, n不删除
-r 删除一个目录(含所有文件), r for repository
-f 强制执行删除操作, f for force
参数可叠加， 如rm -rf  【dir】，直接删除目录
```



### 四个区域：

**工作区（Working Directory）**

就是你在电脑里能实际看到的目录

**暂存区（Stage/Index）**

暂存区也叫索引，用来临时存放未提交的内容，一般在.git目录下的index中

**本地仓库（Repository）**

Git在本地的版本库，仓库信息存储在.git这个隐藏目录中

**远程仓库（Remote Repository）**

托管在远程服务器上的仓库。常用的有GitHub、GitLab、Gitee

![72743133770](C:\Users\13518\AppData\Local\Temp\1727431337700.png)

### Git的三种状态

- 已修改（Modified）

  修改了但是未保存到暂存区的文件

- 已暂存（Staged）

  修改后已经保存到暂存区的文件

- 已提交（Committed）

  把暂存区的文件提交到本地仓库后的状态

![72743166106](C:\Users\13518\AppData\Local\Temp\1727431661067.png)

### 添加和提交文件

**查看仓库状态：**

git status

**将文件添加到暂存区，等待后续提交操作：**

git add

​	**通配符命令**

​	git add *.txt

​	将所有txt结尾的文件添加到暂存区

​	**文件夹参数**(使用目录)

​	git add .

​	将当前文件夹下的所有文件都添加到暂存区里

​	注意相对路径

​	**文件名**

**将文件从暂存区提交到仓库中：**

git commit -m  "提交你干什么的信息"

>只会提交暂存区内容，工作区中文件不会提交
>
>若不指定-m的参数，那么git commit命令会进入一个交互式的界面，默认会使用vim（强大的文本编辑器）来编辑提交信息

**补充vim：**

使用方向键来移动光标

使用i键进入编辑模式，输入提交信息

使用esc键回到命令模式

输入    :wq    保存退出，提交就完成了

**查看仓库历史提交记录：**

git log

id（commit后面的16进制字符串）、每次提交到作者、邮箱、提交时间、之前编写的注释信息等内容

git log --oneline（简洁版）

只能看到ID和提交的注释信息



### git reset（作用：回退版本，并保留或丢弃工作区、暂存区内容）

![72743350513](C:\Users\13518\AppData\Local\Temp\1727433505136.png)

> hard硬撤回，慎用
>
> 若误用，则回溯（1.使用git reflog命令来查看一下操作的历史记录，找到误操作前的版本号，然后再使用git reset命令来回退到这个版本就可以了
>
> mixed默认，可以不输

**How回退到上一版本：**

法一：git reset --（选） 版本ID

例如：git reset --soft 5af90b8

法二：git reset --（选） HEAD^

例如：git reset --hard HEAD^



### git diff

![72743694731](C:\Users\13518\AppData\Local\Temp\1727436947313.png)

