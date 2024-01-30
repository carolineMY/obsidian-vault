### 基础命令

git init  初始化git项目，生成.git文件

git add *

git pull 

git fetch 更新关联关系、分支，不拉取具体变化

git commit -m 'init'

git statsh 暂存更改的代码

git stash pop 弹出上次暂存的代码

git branch 查看当前分支

git branch -a 查看所有分支

git checkout master 切换到master分支

git checkout -b release-1.2.1 新建并切换到分支

git push -u  本地仓库关联到远程仓库

git log --author=Caroline --since=2023-01-01 --until=2023-12-26 --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }'
查询某段时间代码提交记录

git checkout -b dev --track origin/dev 创建本地分支dev,并关联到远程分支origin/dev

git  config core.ignorecase false  提交文件到仓库时不忽略大小写，即区分大小写
git  config core.ignorecase true  提交文件到仓库时忽略大小写，即不区分大小写