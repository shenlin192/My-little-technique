# Git 学习笔记

* [Git 基本知识](#1)

* [git本地仓库控制](#2)

* [git本地仓库控制](#3)



<h2 id="1">Git 基本知识</h2>
 
git是一种版本控制工具，能控制本地仓库和远程仓库。

git的本地仓库由的三个区组成:

1. **工作区**（working area），它持有实际文件；
2. **暂存区**（Index），它像个缓存区域，临时保存你的改动；（在.git index 文件中)
3. **HEAD**，它指向最后一次commit的结果。
放在暂存区（add）的文件修改容易，放在仓库（commit）里的文件修改困难。

只有在有 .git 隐藏文件的地方才有能运行git 命令


<h2 id="2"> git本地仓库控制</h2>

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

5 分支
  - git branch /<branch_name> 增加分支
  - git branch 查看分支
  - git checkout branch_name 切换分支
分支本质上是指向不同commit版本的指针

6 git log （用于查看当前分支的不同版本号）
	提交的版本号  
	作者 邮件  
	日期  
		注释
		
![](https://github.com/shenlin192/git_instruction/blob/master/git_log.PNG)



<h2 id="3"> git远程仓库版本控制</h2>

	* [使用SSH公钥和私钥](#3.1)
	
	* [克隆项目后，本地操作，再推送上去](#3.2)
	
	* [多人协作使用git](#3.3)
	
	* [杂项](#3.4)


git 服务器支持 SSH HTTP GIT协议

SSH GIT协议都是智能协议（可以看到传输进度与速度）
HTTP 智能协议或哑协议都行

<h3 id="3.1">使用SSH公钥和私钥</h3>

 1首先我们要用SSH 命令生成公钥和私钥
 
 `ssh-keygen -t rsa -C "自己配置的邮箱"`
 
 /**** ssh-keygen -t rsa -C "shenlin192@gmail.com" ****/
 
 然后设置生成的公钥与私钥的存储路径
 
 bug： 要先有 rsa 文件才可以在git bash中对其重写
 如果觉得麻烦就直接保存在默认路径中“/c/Users/shenlin/.ssh/id_rsa ”

 2然后登陆github 
 在头像旁边可以有个按钮可以选择setting->SSH keys-> New SSH key
 将步骤a 中得到的公钥用文本编辑器打开，再复制粘贴到github上
 最后用命令：
 `ssh git@github.com `
 测试这个公钥是否能用

 /\*\*\*\*\*此时就可以用shenlin192这个用户名跟github交互了\*\*\*\*\*/
 
 使用SSH的好处是每次push都不需要输入用户名和密码
 在用户设置中设置SSH，拥有私钥的人可以对用户所有仓库进行修改
 在项目中设置SSH，拥有私钥的人可以对仓库进行修改 


<h3 id="3.2">克隆项目后，本地操作，再推送上去</h3>

 1git clone <项目地址> 
 此时就会把远程项目复制到本机（同时也把.git文件配置好了）
 若是打开.git 中的 .config 文件则会看到远程分支"origin"
 及其地址url。同时本地“master”跟远程的“origin”自动关联起来了
 
`
[remote "origin"]

	url = https://github.com/Valars/Hyblab2016.git
	
	fetch = +refs/heads/*:refs/remotes/origin/*
	
[branch "master"]

	remote = origin
	
	merge = refs/heads/master
`

 /\*\*实际上，想要本地仓库与远程仓库关联只需要修改.config中的url即可\*\*/

 2 
 在本机对项目文件修改完成后，使用 git add 和 git commit 命令
 将修改好的文件保存在本机仓库中。然后再用以下命令push到远程服务器
   
   `git push -u [remote branch] [local branch]`
   
   `git push -u origin master`
   
 若是简写 git push 那么就会执行默认参数，
 远程分支就是.config中remote的内容
 本地分支就是当前工作分支


<h3 id="3.3">多人协作使用git</h3>
 
 在github的仓库选择->setting->collaborators 就可以邀请协作者了
 

 - git fetch <remote repository> 将远程服务器的信息抓取到本地仓库中但不影响工作区 
 - git merge 远程仓库名/分支名      将远程仓库分支合并到工作区
 - git pull= git fetch+git merge 
 
 若合并成功（没出现本地和远程仓库都对同一文件同一地方进行修改），则可以puch。
 若合并不成功，则需要人工解决进行合并，人工合并完才能push。
 这就相当于 git 强制要求你阅读远程仓库的变化。

<h3 id="3.4">杂项</h3>
 git branch -vv 查看本地分支和远程分支的关系
