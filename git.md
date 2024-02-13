```git init
git init name

git add

git diff 
git diff HEAD~ HEAD
git diff HEAD~2 HEAD
git diff HEAD~3 HEAD file3

rm file1.txt
git ls-files
git add file1.txt
git rm file2.txt

.gitignore


```

# Git分布式管理控制工具

Git的应用场景：

1. 备份
2. 代码还原
3. 协同开发
4. 追溯问题代码的编写人和编写时间

版本控制工具：

1. 集中式版本控制工具

   版本库是集中存放在中央服务器的，team里每个人work时从中央服务器下载代码，必须联网才能工作，局域网或互联网，个人修改后提交到中央版本库。

2. 分布式版本控制工具

   没有中央服务器，每个人的电脑上都是一个完整的版本库。



## 1. Git环境

### 1.1 git基本配置

配置基本信息：

```
git config --global user.name "user.name"
git confit --global user.email "user.email"
```

查看配置信息：

```
git config --global user.name
git confit --global
user.email
```

### 1.2 为常用指令配置别名

1. 打开用户目录，创建`.bashrc`文件

   用户目录位于`C:\Users\lenovo`

   在该目录下创建文件：`touch ~/.bashrc

2. 在.bashrc文件中输入内容

   ```shell
   #用于输出git提交日志
   alias git-log='git log --pretty=oneline --all --graph --abbrev-commit'
   #用于输出当前目录所有文件及其基本信息
   alias ll='ls -al'
   ```

   

## 2. 本地仓库

1. 在电脑的任意位置创建一个空目录（例如test）作为我们的本地git仓库
2. 进入这个目录中，点击右键打开git bash
3. 执行命令git init
4. 如果创建成功可以在文件夹下面看到隐藏的.git目录

## 3. 基础操作指令

三个位置：仓库（repository），暂存区（index），工作区（workspace）

文件在这三个状态间的转换

### 3.1 查看修改的状态

```
git status
```

### 3.2 添加工作区到暂存区

```
git add . //将工作区的所有文件都添加到暂存区
git add filename
```



### 3.3 提交暂存区到本地仓库

```
git commit -m"注释内容"
```

### 3.4 查看提交日志

- 作用：查看提交记录

- 命令形式：git log [option]
  - option
    - --all 显示所有分支
    - --pretty=oneline 将提交信息显示为一行
    - --abbrev-commit 使得输出的commitld更剪短
    - --graph 以图的方式显示

一般所有选项都加上。

### 3.5 版本回退

```
git reset -hard commitID
//commitID可以用git-log或者git log查看
```

通过`git reflog`查看已经删除的记录

### 3.6 添加文件至忽略列表

一般我们总会有些文件无需纳入Git的管理，也不希望它们总出现在未跟踪文件列表，通常都是些自动生成的文件，比如说日志文件，或者编译过程中创建的临时文件等，在这种情况下，我们可以在工作目录中创建一个名为.gitignore的文件，列出要忽略的文件格式。

## 4. 分支

使用分支意味着你可以把我们的工作从开发主线上分离出来进行重大bug修改，开发新的功能，以免影响开发主线。

git branch：查看分支

git branch "branch name"：新建新分支

git checkout "branch name"：切换分支

git checkout -b "branch name"：新建分支，并切换

git merge "branch name"：合并分支，一般是合并入master分支

git branch -d "branch name"：删除分支

git branch -D "branch name"：强制删除分支

（ 当某一个分支没有完全merge时，删除会提示）

删除分支不能删除当前分支

### 解决冲突

当两个分支上对文件的修改可能会存在冲突，例如同时修改了同一个文件的同一行，这时就需要手动解决冲突，解决冲突的步骤：

1. 处理文件中冲突的地方
2. 将解决玩冲突的文件加入到暂存区
3. 提交到仓库

### 开发中分支使用的原则与流程

- master（生产）分支

  线上分支，主分支，中小规模项目作为线上运行的应用对应的分支

- develop（开发）分支

  是从master创建的分支，一般作为开发部门的主要开发分支，如果没有其他并行开发不同期上线要求，都可以在此版本进行开发，阶段开发完成后，需要合并到master分支准备上线

- feature分支

  从develop创建的分支，一般是同期并行开发，但不同期上线创建的分支，分支上的研发任务完成后合并到develop分支

- hotfix分支

  从master派生的分支，一般作为线上bug修复使用，修复完成后需要合并到master，test，develop分支

- 其他分支，test，pre等

## 5. Git远程仓库

