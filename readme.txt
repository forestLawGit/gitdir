centos 7 安装git得命令如下：
yum install perl openssh git

创建一个git仓库，需要选择一个合适得地方，创建一个空目录
当前得git仓库目录为：/home/forest/gitdir

通过如下命令把当前目录变为Git可以管理得仓库
git init
创建成功后，当前目录下会多一个.git得目录，这个目录是用来管理追踪git仓库得，没事别动，如果看不到，是因为默认是隐藏得，使用ls -ah命令可以查看
