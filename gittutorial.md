# git命令行使用教程
[toc]
## 1 概述  
## 2 Git常用命令  
### 2.1 Git环境配置  
#### 2.1.1 基本配置  
1）打开Git Bash  
2）设置用户信息  
 <p> git config --global user.name "yourname" <p>
 <p> git config --global user.email "your email" <p>  

>查看用户信息  
> <p> git config --global user.name "yourname"  <p>
> <p> git config --global user.email "your email" <p>
#### 2.1.2 为常用指令配置别名
有些指令使用频繁，但是指令非常长，我们可以给这些指令设置别名
1）打开用户目录，**在目录下**GitBash执行`touch ~/.bashrc`
2）在`.bashrc`文件中输入`alias 设置的快捷指令='原指令' `  

如：

![\3.png](3.png "设置git-log")
### 2.2 创建一个<u>本地仓库</u>（repository）
 要使用Git对项目进行版本控制，我们需要先使用`git init`初始化
 1）在项目目录下打开GitBash
 2）执行命令`git init`

此时在该目录下会出现隐藏的`.git`目录

![](4.png "使用git init对本地项目进行托管")
### 2.3 基础操作指令
Git工作目录下对文件的**修改**（增加、删除、更新）会存在几个状态，这些**修改**的状态会随着我们执行Git命令而发生变化。

![5.png](5.png )

### 📌2.3.1 查看修改的状态(status)
- 作用：查看<u>工作区</u>（workspace）或者<u>暂存区</u>(index)的状态
- 命令形式：`git status`
### 📌2.3.2 将工作区内容添加到暂存区(add)
- 作用：添加工作区一个或者多个文件的修改到暂存区
- 命令形式：`git add 单个文件名|通配符`
    - 将所有修改加入暂存区：`git add .`
    - 若需要取消git对某些文件或者文件夹更改的跟踪，需要在项目目录下新建`.gitignore`文件，并写入需要取消跟踪的文件的相对路径。详细内容见[2.3.6 添加文件至忽略列表](#236-添加文件至忽略列表)
### 📌2.3.3 提交暂存区到本地仓库（commit）
- 作用：提交暂存区内容到本地仓库的当前分支
- 命令形式：`git commit -m "注释内容"`
### 📌2.3.4 查看提交日志（log）
- 作用：查看提交记录
- 命令形式：`git log [option]`
    - options
        - `--all` 显示所有分支
        - `--pretty=ontline` 将提交信息显示为一行
        - `--graph` 以图的形式显示
>在2.1.2 为常用指令配置别名`**git-log**就包含了这个参数，所以后续可以直接使用指令**git-log**替代

### 📌2.3.5 版本回退
- 作用：版本切换
- 命令形式：`git reset --hard commitID`
    commitID可以用`git-log`或者`git log`指令查看
>如果要查看已经删除的记录，可以使用`git reflog`
### 2.3.6 添加文件至忽略列表
