# git学习

[Git教程 - 廖雪峰的官方网站](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)

## 安装后设置名称和email地址

```git
$ git config --global user.name "Your Name"
$ git config --global user.email "email@example.com"
```

`--golobal`表示是全局设置，可以不使用这个，表示只在项目内生效。


## 创建版本库、添加、修改文件、commit并提交

### 本地创建一个版本库

创建一个目录，进入此目录使用`git init`命令即可。

```
mkdir learngit
cd learngit
git init
```

其中`mkdir`命令为在当前目录下创建一个文件夹。

### 将文件添加到仓库

使用`git add 文件名`即可。

```
git add atom.md
```

### 进行commit

使用`commit`命令即可（省略前面的`git`了，所有的`git`命令都以`git`开始），并使用`-m "commit描述"`命令添加本次提交的描述信息。

```
git commit -m "add readme file"
```

> 每次commit前都需要先添加修改的文件，即先使用`add`命令，再使用`commit`命令。

### 查看状态

使用`status`命令即可。

```git:n
git status
# On branch master
# Your branch is up-to-date with 'origin/master'.
# Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)

        modified:   README.md

# no changes added to commit (use "git add" and/or "git commit -a")

```
上面命令可以知道*README.md*文件被修改过。

还可以使用`diff`命令查看修改的具体内容。




### 推送

提交到远程仓库的前提是：

1. 远程已经建立仓库
2. 账户或ssh已配置好  
3.