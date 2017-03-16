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

此命令对比的是我们的工作区`working copy` 和 暂存区 `index` 或称为 `stage`。

还可以使用`diff`命令查看修改的具体内容。




### 推送

提交到远程仓库的前提是：

1. 远程已经建立仓库
2. 账户或ssh已配置好  
3. 本地仓库已经和远程关联。

第一次推送时，加入 `-u`命令，后面加上 远端仓库 和 分支。 推送之后会自动讲本地的分支和远端进行关联。

之后的提交直接使用`git push`即可。

```git:n
git push -u origin master
```

## 状态管理

### 版本之前的切换，未推送到远端

每一个commit都是一个版本，我们可以使用`git log`命令来查看版本历史，使用` git reset`命令来实现版本的切换。
比较有用的是Git提供了一个命令`git reflog`用来记录我们所做的每一次命令。

```git:n
# 回退到上个版本
git reset --hard HEAD^ 
# 回退到上上个版本
git reset --hard HEAD^^ 
# 回退到往前第50个版本
git reset --hard HEAD~50

# 到 commit id为 3628164 的版本 id不用写全 前几位就可以，会自动查找。
git reset --hard 3628164
```

上面的`--hard`参数位置另外两个值分别是 `soft` 和 `mixed`，其中`mixed` 为默认值。

- `soft` : 仅仅重置 HEAD 到指定的commit， index 和  working copy 都不会变化。

- `hard` : 重置所有，HEAD、index、working copy 都回到指定的版本，可能存在都是数据的危险，但却是唯一能回退working copy的操作。

- `mixed` ：此为默认， 重置HEAD和index，working copy不受影响。

> git 的管理机制是这样的： 
> - working copy 为我们看到的，直接修改的文件。 
> - index 或称为 stage 为暂存区。 
> - HEAD 可简单理解为版本库 
> - 我们修改文件，并且 git add 之后 修改内容将放入 index  
> - 当我们执行 git commit 后
将index内的所有修改 移入版本库 ，index清空。 
> 参考链接 
> - [git reset
soft,hard,mixed之区别深解](http://www.cnblogs.com/kidsitcn/p/4513297.html)
> - [git
工作区和暂存区](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/0013745374151782eb658c5a5ca454eaa451661275886c6000)


### 撤销修改

命令`git checkout -- readme.txt`意思就是，把`readme.txt`文件在工作区的修改全部撤销，这里有两种情况：

一种是`readme.txt`自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；

一种是`readme.txt`已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。

总之，就是让这个文件回到最近一次`git commit`或`git add`时的状态。

> 注意不要忘记 `--` 否则，`git checkout` 命令就成了切换分支的命令。
