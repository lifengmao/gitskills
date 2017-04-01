# Git 教程 By 廖雪峰

http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000

---

## 创建版本库

首先，选择一个合适的地方，创建一个空目录：

    $ mkdir learngit
$ cd learngit
    $ pwd
    /Users/michael/learngi
    
    
第二步，通过git init命令把这个目录变成Git可以管理的仓库：

> git init

当前目录会多一个.git目录，说明仓库已经建好。

## 添加文件

第一步 用git add 告诉git，把文件添加到仓库(假设文件是readme.txt)：

    git add readme.txt
    
第二步 用git commit 告诉git,把文件提交到仓库

    git commit -m "这里可以填写文件更改的信息"
    
要随时掌握工作区的状态，使用git status命令

    git status
    
如果git status告诉你有文件被修改，可以使用git diff 查看修改内容

    git diff readme.txt
    
## 版本回退

使用git reset可以实现版本的回退

    git reset --hard HEAD^
    
HEAD^表示上一个版本，相应的HEAD^^表示上一个版本的上一个版本。 可以使用git log 查看提交的信息

    git log
    
可以查看每次提交信息的commit id 使用这个id可以将版本回退到与id相应的版本

    git reset --hard commit id
   
## 工作区和暂存区
   
   当我们使用git add时，实际上就是把文件修改添加到暂存区
   当我们用git commit时，实际上就是把暂存区的所有内容提交到当前分支。
   
## 撤销修改

当我们需要把文件的修改撤销时，如果该文件还未提交到当前分支，可以使用git checkout进行撤销

    git checkout -- fileName

其中fileName是你想撤销的文件名称，它会回退到最近一次git commit或者git add时的状态

## 删除文件

可以使用rm命令将文件删除

   git rm fileName
   git commit -m "删除文件"
   
## 建立远程仓库

第一步：创建ssh Key 

    ssh-keygen -t rsa -C "youremail@example.com"
    
如果一切顺利的话，可以在用户主目录里找到.ssh目录，里面有id_rsa和id_rsa.pub两个文件，这两个就是SSH Key的秘钥对，id_rsa是私钥，不能泄露出去，id_rsa.pub是公钥，可以放心地告诉任何人。

第二步： 登陆GitHub，打开“Account settings”，“SSH Keys”页面：

然后，点“Add SSH Key”，填上任意Title，在Key文本框里粘贴id_rsa.pub文件的内容，点“Add Key”，你就应该看到已经添加的Key

## 添加远程仓库

首先，登陆GitHub，然后，在右上角找到“Create a new repo”按钮，创建一个新的仓库

在Repository name填入learngit，其他保持默认设置，点击“Create repository”按钮，就成功地创建了一个新的Git仓库

目前，在GitHub上的这个learngit仓库还是空的，GitHub告诉我们，可以从这个仓库克隆出新的仓库，也可以把一个已有的本地仓库与之关联，然后，把本地仓库的内容推送到GitHub仓库。

我们根据GitHub的提示，在本地的learngit仓库下运行命令：

    git remote add origin git@github.com:michaelliao/learngit.git
    
下一步，就可以把本地库的所有内容推送到远程库上：

    git push -u origin master

## 从远程库克隆

使用git clone可以将远程仓库克隆到本地

    git clone git@github.com:michaelliao/gitskills.git
    
## 创建于合并分支

    git checkout -b dev
    相当于
    git branch dev
    git checkout dev
    
可以使用git branch查看分支

    git branch

可以使用git merge 合并分支

    git merge dev

合并完成后，可以删除该分支

    git branch -d dev

