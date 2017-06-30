# git 教程
## git 简介
```
分布式版本控制和源代码管理系统。
Linux 开源内核，是由很多人共同开发的，git 的产生，最初是为了给Linux 内核管理源码的。

特点： 
1，git 是分布式的版本管理系统，团队内成员可以很好的并行地开发各个模块的功能。
2，git 可以很好的进行版本管理，可以方便的回溯到任何一个版本。
   （版本管理： 一般上，例如项目开发了某个功能点，并且这个功能点测试通过了，整个项目中可以作为一个过程中的版本，
     这个版本，是可用的，我们则对这个特殊的版本进行管理，一般上是可以给这个阶段的代码打Tag， git tag）
3，git 利用第三方githup 作为服务器，几乎不会出现向svn 一样的中央库服务不可用的问题。
4，可以方便的去掉有开发平台，例如IEDA 或者eclipse 中生成的文件，或者一些编译产生的文件，只保留一分纯净的代码
   （git 中，只要在git 仓库根目录中添加一个.gitignore 文件，把不需要的文件在git add 的时候过滤掉即可）
5，git 引入branch 的概念，可以多个主线一起开发（见多的大多的项目，一般只有一个master 主线），也可能针对一分基本的代码，
    各个局点所不同的时候，可以轻松的引入多个分支。
```
## git安装（客户端的安装）
[git官网，跳转](https://git-scm.com/)
```
完整意义上说，应该是git 客户端的安装。
客户端安装，linux 的一般用不上，如果用到，请参考网上的教程
windows 下的安装，请直接到上面的链接git 官网下载安装：
```

## 注册githup 账号，创建git 主仓库
[githup 官网](github.com)
```
git 可以自己利用一台机器搭建git 服务器，但是相对中小型公司来说，
这样维护起来比较麻烦，而且容易出现git 服务器坏掉的情况，
所以，比较常见的方式是托管到第三方的的git 服务器，比如githup 

githup ，一个git 仓库的服务器， 仓库可以托管到githup 上。
1，到githup 上注册一个账号，
2，账号注册好后，可以创建git 主仓库
（一般在页面的右上角有一个加号的地方，点击则有 Import repository 和 new repository 等选项）

```

## 初始化git 客户端
```
在windows 上打开Git Bash
(一般在所有程序里可以找到，或者直接在桌面上，右键----> Git Bash)

然后执行如下两个命令:
git config --global  user.email "注册的邮箱账号"
git config --global user.name "git 账号用户名"

为了让之后向 githup  push 的时候免密码
在git bash 执行如下命令
ssh-keygen -t rsa -C "your email or your computer name"
提示输入密码 或者目录部分，不用操作，直接回车

执行后，会在 用户目录下， 比如C:/Users/ldl/.ssh 下
生成两个文件id_rsa（私钥） 和id_rsa.pub（公钥）    （如果没有看到后缀，请设置文件系统里的查看，不要隐藏已知的后缀名）
用文本编辑器打开 id_rsa.pub， 把里面的内容拷贝到githup 的 settings 下的sshkey 模块中。
```

## git经典源码管理和版本维护开发应用模型
![git_module](https://github.com/hzgosun/KMap/blob/master/Picture/Git/git_developer_modle_for_team_menbers.gif)  
[!参考链接](https://guides.github.com/introduction/flow/?utm_source=onboarding-series&utm_medium=email&utm_content=read-the-guide-cta&utm_campaign=learn-github-flow-email)



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

## git 常用命令

```
创建仓库，有两种办法：
1， 一个是直接在任意一个目录下面执行，执行如下命令
   git init
2， 另外，可以直接 git clone 代码到本地。



3，查看历史修改记录：
git log 
可以加参数：
lenovo@lenovo-PC MINGW64 ~/Desktop/Kmap (master)
$ git log --graph  --oneline
* 3a337cf (HEAD -> master, origin/master, origin/HEAD) to add file of 经典开发版本管理和源码管理模型
* 476904e Update Git简单教程.md
* fd397b4 Update Git简单教程.md
* 5c97295 Update Git简单教程.md
* 0edfe6b Create Git简单教程.md
* 2d1bc9a to change git_work_flow.git
* 3ebd006 to add git_flow.jpg
* 9364511 to add KMap excel
* a26da9d to delete unuse file
* 4155f84 to add hadoop file
* 1473cca Delete TmpFile.md
* f888eba to init the repository.
* 98a724c Create README.md

4，回复到某一个修改的版本
两种方式，
git reset 2d1bc9a （git log 中，前面得出的一串号码）
git reset --hard 2d1bc9a

一个特殊的用法， git reset   后面不跟任何内容，则放弃当前添加到暂存区的内容

5，添加到暂存区
git  add  <file>
git add --all

6, 提交修改到仓库即，.git 文件夹
仓库中只保存了文件的改动情况，所以.git 文件夹不可以动，要不然会找不到历史的版本。
git commit -m "这次提交修改的原因，修改的内容，写清楚"


7，克隆和拉取，推送
git clone **.git
git push origin master
git pull origin master

8, 显示仓库别名
git remote -v 


9,git status 
查看，现在的工作目录的状态


```
## git 对冲突的处理
```
6，git 对冲突的处理： 
   git 的主库，一般上是因为个人的本地的代码，和主库的代码，修改的的是同一个文件的同一个地方， 
   或者git push 的 时候出现push 失败
   提示错误类似如下：
   To github.com:easesstone/knowledge.git
   ! [rejected]        master -> master (non-fast-forward)
   error: failed to push some refs to 'git@github.com:easesstone/knowledge.git'
   hint: Updates were rejected because the tip of your current branch is behind
   hint: its remote counterpart. Integrate the remote changes (e.g.
   hint: 'git pull ...') before pushing again.
   hint: See the 'Note about fast-forwards' in 'git push --help' for details.
   
   或者git pull 的时候出现冲突：
   
```


