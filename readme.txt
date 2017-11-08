centos 7 安装git得命令如下：


yum install perl openssh git

创建一个git仓库，需要选择一个合适得地方，创建一个空目录
当前得git仓库目录为：/home/forest/gitdir

通过如下命令把当前目录变为Git可以管理得仓库
git init
创建成功后，当前目录下会多一个.git得目录，这个目录是用来管理追踪git仓库得，没事别动，如果看不到，是因为默认是隐藏得，使用ls -ah命令可以查看

一定要将编写得文件放在仓库目录下，子目录也行。因为GIT是一个仓库，放到其它地方，GIT再厉害也找不到
第一步：通过git add 命令告诉git，把文件添加到仓库：
例子：
 git add readme.txt
第二步: 使用git commit告诉git,把文件提交到仓库
例子：
 git commit
 
查看修改日志使用如下命令:
git log
如果只想在一行中展示，可以使用如下得命令:
git log --pretty=oneline


GIT和其他版本控制系统如SVN的一个不同之处就是暂存区的概念
工作区：就是在你电脑里能够看到的目录，比如当前目录gitdir
版本库：工作区中有一个隐藏目录.git，这个 不算工作区，而是git的版本库
git的版本库里存了很多东西，其中最重要的就是称为stage（暂存区）区，还有GIT自动为我们创建一个分支master，以及指向master的一个指针叫HEAD


git status 查看文件状态


现在，假定你已经完全掌握了暂存区的概念。下面，我们要讨论的就是，为什么Git比其他版本控制系统设计得优秀，因为Git跟踪并管理的是修改，而非文件。
第一次修改 -> git add -> 第二次修改 -> git commit
你看，我们前面讲了，Git管理的是修改，当你用git add命令后，在工作区的第一次修改被放入暂存区，准备提交，但是，在工作区的第二次修改并没有放入暂存区，所以，git commit只负责把暂存区的修改提交了，也就是第一次的修改被提交了，第二次的修改不会被提交。




命令git checkout -- readme.txt意思就是，把readme.txt文件在工作区的修改全部撤销，这里有两种情况：
一种是readme.txt自修改后还没有被放到暂存区，现在，撤销修改就回到和版本库一模一样的状态；
一种是readme.txt已经添加到暂存区后，又作了修改，现在，撤销修改就回到添加到暂存区后的状态。
总之，就是让这个文件回到最近一次git commit或git add时的状态。


在commit之前，你发现了这个问题。用git status查看一下，修改只是添加到了暂存区，还没有提交
Git同样告诉我们，用命令git reset HEAD file可以把暂存区的修改撤销掉（unstage），重新放回工作区
git reset命令既可以回退版本，也可以把暂存区的修改回退到工作区。当我们用HEAD时，表示最新的版本。


场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令git checkout -- file。
场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令git reset HEAD file，就回到了场景1，第二步按场景1操作。
场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。









https://github.com/forestLawGit/gitdir.git

create a new repository on the command line
echo "# gitdir" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/forestLawGit/gitdir.git
git push -u origin master




push an existing repository from the command line
git remote add origin https://github.com/forestLawGit/gitdir.git
git push -u origin master



把本地仓库的内容推送到GitHub仓库。
现在，我们根据GitHub的提示，在本地的learngit仓库下运行命令：
git remote add origin https://github.com/forestLawGit/gitdir.git
请千万注意，把上面的forestLawGit替换成你自己的GitHub账户名，否则，你在本地关联的就是我的远程库，关联没有问题，但是你以后推送是推不上去的，因为你的SSH Key公钥不在我的账户列表中。
添加后，远程库的名字就是origin，这是Git默认的叫法，也可以改成别的，但是origin这个名字一看就知道是远程库

下一步，就可以把本地库的所有内容推送到远程库上：
$ git push -u origin master
把本地库的内容推送到远程，用git push命令，实际上是把当前分支master推送到远程。
由于远程库是空的，我们第一次推送master分支时，加上了-u参数，Git不但会把本地的master分支内容推送的远程新的master分支，还会把本地的master分支和远程的master分支关联起来，在以后的推送或者拉取时就可以简化命令。
推送成功后，可以立刻在GitHub页面中看到远程库的内容已经和本地一模一样：
从现在起，只要本地作了提交，就可以通过命令：
$ git push origin master
把本地master分支的最新修改推送至GitHub，现在，你就拥有了真正的分布式版本库！



