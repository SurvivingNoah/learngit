Git is a discontributed  version control system.
Git is a free software under the GPL.
Git has a mutable index called stage.

git is a distributed version control system.

一、setup
sudo apt-get install  git


二、仓库管理
1.Create a new repository
首先创建一个新目录：
$ mkdir learngit
$ cd learngit

然后变成git仓库
$ git init


2.添加文件到仓库 two steps
$ git add readme.txt

$ git commit -m ' 本次commit的说明  '

$ git checkout -- file
(可以丢弃工作区的修改,总之，就是让文件回到最近一次git commit或git add时的状态。)
(git checkout其实是用版本库里的版本替换工作区的版本，无论工作区是修改还是删除，都可以“一键还原”。)

$ git reset HEAD <file>
(可以把暂存区的修改撤销掉（unstage），重新放回工作区)


3.常用命令
$ git status
( 时刻掌握仓库当前状态)


$ git diff  'filesname'
(查看difference)



三、版本控制管理
$ git log
(查看历史版本)

$ git reflog
(记录你的每一次命令)

1.本地版本控制
在Git中，用HEAD表示当前版本，上一个版本就是HEAD^，上上一个版本就是HEAD^^
回退到上一个版本：
$ git reset --hard HEAD^/或者版本号
HEAD is now at e475afc add distributed


2.版本控制原理
Working Directory   git add到  stage   git commit到  版本分支branch
                    git rm             git commit
    


3.远程仓库管理控制
$ git remote add origin git@github.com:michaelliao/learngit.git
（关联远程库,origin是默认的远程库写法）

$ git push -u origin master
(将本地库的master分支推送到远程库的master分支，-u参数把本地的master分支和远程的master分支关联起来)

$ git push origin master
(只要本地commit到本地仓库后，就可用此命令把本地master分支的最新修改推送至Github中的远程库。)

$ git clone git仓库地址
（从远程仓库克隆到本地仓库）

  
四、branch管理
1.创建、合并与删除分支
$ git branch 查看分支
$ git branch <name>  创建分支
$ git checkout <name>  切换分支
$ git checkout -b <name> 创建并切换分支
$ git merge <name>   合并某分支到当前分支
$ git branch -d <name>  删除某分支

2.解决冲突
当Git无法自动合并分支时：首先解决冲突，再提交，合并完成。

解决冲突就是把Git合并失败的文件手动编辑为我们希望的内容，再提交。


用git log --graph命令可以看到分支合并图。

3.branches策略，Bug Branch,Feature Branch



五.多人协作
查看远程库信息  $ git  remote -v


首先，可以试图用git push origin <branch-name>推送自己的修改；

如果推送失败，则因为远程分支比你的本地更新，需要先用git pull试图合并；

如果合并有冲突，则解决冲突，并在本地提交；

没有冲突或者解决掉冲突后，再用git push origin <branch-name>推送就能成功！

如果git pull提示no tracking information，则说明本地分支和远程分支的链接关系没有创建，用命令git branch --set-upstream-to <branch-name> origin/<branch-name>。
