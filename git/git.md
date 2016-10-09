# Study1
## git学习(Bash)
### 1、git init：初始化仓库
		在需要使用git来管理的项目目录中，使用此命令来初始化仓库。
### 2、git status：查看仓库的状态
### 3、git add：向暂存区中添加文件
	git add .：一次性加入当前目录中的全部文件
	git add –i: 使用互动模式来提交文件
### 4、git	commit：保存仓库的历史纪录
### 5、git diff：查看工作树与暂存区的差别
### 6、git diff HEAD：查看工作树与最新提交的差别
### 7、git log：查看提交日志
   git log --pretty=short：只显示提交信息的第一行
   git log 文件名：只显示指定目录、文件的日志
   git log -p 文件名：显示指定文件的改动，查看提交所带来的影响
### 8、git branch：显示分支览表，将会列出当前所有分支，左侧标有*表示当前所在分支
   git checkout –b 分支名称：创建、切换分支，若分支存在，则直接切换，若分支不存在则创建并切换，
   等同于：
   git branch 分支名称
   git checkout 分支名称
### 9、git merge：合并分支
### 10、git remote add：添加远程仓库
   git remote add 主机名 远程仓库的地址，之后就可以使用主机名来代替远程仓库
   git push -u 主机名 master：将master分支提交的历史记录推送至远程仓库GitHub
   git checkout -b 新的分支名称 主机名/要下载到本地的分支名称：
	将远程仓库的某个分支中的文件下载到本地(本地没有此分支)
   git remote：列出所有远程主机。
   git remote -v：列出所有主机的名称和对应的网址
   git remote show 主机名：可以查看该主机的详细信息
   git remote rm 主机名：删除远程主机
   git remote rename 机原主名 新主机名：对远程主机的改名
### 11、git reflog：查看当前仓库执行过的操作的日志，会显示当前仓库所有操作和对应的哈希值，可以使用下面命令
   git reset --hard 哈希值：推进至历史的某个状态
### 12、git pull：获取最新的远程仓库分支
   git pull 主机名 远程分支名称：本地分支名称：  从远程仓库获取最新的此分支的最新状态与本地的分支合并。
### 13、git push:将本地分支的更新，推送到远程主机。
   git push 主机名 本地分支名称：远程主机名称：  将本地仓库的某个分支与远程主机的某个分支合并。
### 14、git clone 版本库地址：直接从远程仓库下载一个新的项目(本地没有此项目)
   该命令会在本地主机生成一个目录，与远程主机的版本库同名。
   $ git clone https://github.com/WangJieWJ/IntelliJ-IDEA.git
   如果要指定不同的目录名，可以将目录名作为git clone命令的第二个参数。
   $ git clone https://github.com/WangJieWJ/IntelliJ-IDEA.git download
### 15、git fetch 远程主机：取回该远程主机中的所有分支的更新到本地
   git fetch 远程主机名 分支名：取回该远程主机中的特定分支的更新
