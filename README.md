# Git 学习笔记
## Git 基本知识
git是一种版本控制工具，能控制本地仓库和远程仓库。

git的本地仓库由的三个区组成:

1. **工作区**（working area），它持有实际文件；
2. **暂存区**（Index），它像个缓存区域，临时保存你的改动；（在.git index 文件中)
3. **HEAD**，它指向最后一次commit的结果。
放在暂存区（add）的文件修改容易，放在仓库（commit）里的文件修改困难。

只有在有 .git 隐藏文件的地方才有能运行git 命令

## git本地仓库控制
local repository 本地仓库 保存在.git object中
自己跟自己玩 不安全

1 开始工作前 git init 初始化一个空的git仓库。
此时生成 .git 隐藏文件夹，用于存放版本数据。
只有在有 .git 隐藏文件的地方才有能运行git 命令
不然会有以下错误:

`$ git clone git@github.com:shenlin192/git_instruction.git
fatal: destination path 'git_instruction' already exists and is not an empty directory.`

2 改变用户信息 git config
  - git config --global user.name "SHENLIN"
  - git config --global user.email shenlin192@gmail.com
  - git config -l （查看config的状态）

3 git add 用于将工作区新文件放入 index(staging area)缓存区里
  - git add *.html 所有的html文件
  - git add . 所有文件
  
4 git commit -m 将缓存区文件放入仓库
  
  若文件放入缓存区后再被修改了，则用 
  git commit -am 直接将其放入仓库
  相当于 git add <filename> + git commit -m
  用新修改的文件状态覆盖缓存区中的文件状态+放入仓库
  
  本质上 git 保存不同版本文件的快照
  一个commit就有一个版本，一个版本里面有一个指针，指向 一个blob（二进制大对象） 表 
  （blob表里面有指向项目中各个文件的指针）
  header 指针指向当前版本

5 - git branch <branch_name> 增加分支
  - git branch 查看分支
  - git checkout <branch_name> 切换分支
分支本质上是指向不同commit版本的指针

6 git log （用于查看当前分支的不同版本号）
	提交的版本号
	作者 邮件
	日期
		注释
		


## git远程仓库版本控制

