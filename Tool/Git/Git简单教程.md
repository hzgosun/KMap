# git 教程
## git 简介
```
分布式版本控制和源代码管理系统。
Linux 开源内核，是由很多人共同开发的，git 的产生，最初是为了给Linux 内核管理源码的。
```
## git安装
[git官网，跳转](https://git-scm.com/)
```
完整意义上说，应该是git 客户端的安装。
客户端安装，linux 的一般用不上，如果用到，请参考网上的教程
windows 下的安装，请直接到上面的链接git 官网下载安装：
安装后，
```

## 注册githup 账号，初始化git 客户端配置
[githup 官网](github.com)
```
githup ，一个git 仓库的服务器， 仓库可以托管到githup 上。
1，到githup 上注册一个账号，
2，账号注册好后，
在windows 上打开Git Bash
一般在所有程序里可以找到，或者直接在桌面上，右键----> Git Bash

然后执行如下两个命令:
git config --global  user.email "注册的邮箱账号"
git config --global user.name "git 账号用户名"
```




## git 一些概念
### 1,版本控制：  
维护历史的版本，方便快速的回复到历史中的任何一个版本。  
便于开发人员间的合作，共同开发一个版本的工程。  

### 2，工作区，暂存区，索引（或者可以直接理解为仓库）  
![git_work_flow](https://github.com/hzgosun/KMap/blob/master/Picture/Git/git_work_flow.gif)

### 3,Clone，Init,Branches,PULL,PUSH
```
一般对应着以下的命令：
分别表示从远程克隆代码库，例如：git clone  https://github.com/hzgosun/KMap.git
初始化git 仓库（这个一般用不到）git init
git 的分支：  
    开发是基于分支开发的，有一个主分支，一般以master 分支为主分支，（一般不允许在master 分支上直接修改代码）
    其他的分支，一般为开发的分支，可以任意命令，一般以你开发的这个模块的功能来命名。
    开发分支的代码验证通过后，可以合并到master 的分支。
一下是关于分支的一些常用命令。
git branch -v   (显示所有分支)
git branch <分支名> （新建一个分支）
git checkout <分支名> （切换到新的分支）
git checkout -b <分支名> (新建并且切换到一个新的分支)

PULL  拉取：
从远程仓库拉取代码，
对应着git pull origin master （origin 代表着远程仓库  master 表示远程仓库的主分支）
拉取代码，并且合并到本地库。

PUSH 
推送，把本地commit 的内容，推送到远程仓库，是本地和远程仓库的内容保持一致。 
即 git push orgin master   （origin 表示的是远程仓库， master 表示的是本地的master 分支）
完整形式 git push origin master:master   （把本地的仓库master分支的内容推送到远程仓库的master）

```


## git经典源码管理和版本维护开发应用模型
![git版本管理和源码维护开发模型](/Picture/Git/git_developer_modle_for_team_menbers.git)


