#工作区与版本库
工作区是在PC上可以看到的目录；版本库是在工作区中有一个隐藏的文件夹.git，其中版本库还包含暂存区(stage)以及git自动创建的第一个分支master和指向master的一个指针HEAD。
#初始化仓库
使用git init命令将当前目录初始化成git可以管理的仓库。此时在当前文件夹下会出现一个隐藏的目录.git
#git提交文件的版本库
1. 使用git add filename将文件提交到暂存区
2. 使用git commit -m 'comments'将在暂存区的所有文件提交到当前分支
#查看修改状态
git只能跟踪所有文本文件的改动，如txt文件、网页、程序等，无法跟踪图片、视频等的改动。
git status命令可以查看文件是否有改动，是否有工作区文件未提交。
git dif filename可以查看文件发生了怎样的改动
#版本回退
回退的是提交后的文件版本。git log命令可以查看提交的历史记录，git log --pretty=oneline可以简略显示提交的日志。
##通过次数回退
git reset --hard HEAD^命令可以回退到提交的上一版本，依次类推回退到上上版本可以使用HEAD^^，如果回退的版本较多，例如回退到前55个版本，可以使用HEAD~55
##通过版本号回退
首先使用git reflog查看提交日志的版本号，版本号类似c695f63。
使用命令git reset --hard+版本号回退到指定版本。
#撤销修改
git checkout -- filename可以丢失对于在工作区文件的修改，撤销的是文件在工作区的所有更改，此时有两种情况：
1. 工作区文件修改后还没有add到暂存区，此时使用撤销命令，就可以回到和版本库一样的状态。
2. 文件已经放入暂存区中，然后进行修改，此时使用撤销命令会回到add到暂存区后的状态。
命令中--非常重要，如果没有--，命令就会变成创建分支的命令。
#删除文件
rm filename删除在版本库中的文件，此时如果commit，则会永久删除文件；此时也可以通过命令git checkout -- filename恢复被删掉的文件。
#将当前分支推送到远程
git remote add origin URL
git push -u origin master第一次推送需要使用-u，不仅可以当前分支内容推送到远程，而且还会使本地分支和远程分支关联起来。
若是出现 failed to push some refs to问题，是因为远程库中的README.md不在本地代码目录中。需要使用命令git pull --rebase origin master进行合并。
然后便可以使用git push origin master命令将本地的更改推送到远程仓库中。
#从远程仓库克隆
使用git clone URL命令将远程仓库内容克隆到本地。

