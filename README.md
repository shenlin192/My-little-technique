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

1. 开始工作前 git init 初始化一个空的git仓库。
此时生成 .git 隐藏文件夹，用于存放版本数据。
只有在有 .git 隐藏文件的地方才有能运行git 命令
不然会有以下错误:

`$ git clone git@github.com:shenlin192/git_instruction.git
fatal: destination path 'git_instruction' already exists and is not an empty directory.`
2. 改变用户信息 git config
  - git config --global user.name "SHENLIN"
  - git config --global user.email shenlin192@gmail.com
  - git config -l （查看config的状态）

3. git add 用于将工作区新文件放入 index(staging area)缓存区里
  - git add *.html 所有的html文件
  - git add . 所有文件




## git远程仓库版本控制

