# git学习

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


### 提交到远程仓库

使用`commit`命令即可（省略前面的`git`了，所有的`git`命令都以`git`开始），并使用`-m "commit描述"`命令添加本次提交的描述信息。





### 推送

提交到远程仓库的前提是：

1. 远程已经建立仓库
2. 账户或ssh已配置好  
3.
