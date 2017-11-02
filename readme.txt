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
