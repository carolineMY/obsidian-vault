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

git cherry-pick 4a2f8a1465b3d94b5ad80d7b4fc6abb09d6f5831 拉取某次提交到当前分支

git push origin release/1.1.1 -u  本地仓库关联到远程仓库

git log --since="2023-01-01" --until="2023-12-31" 查询 2023-01-01 到 2023-12-31 的提交

git log --since="2023-01-01" --until="2023-12-31" --oneline 简化输出（单行显示）

git log --since="2023-01-01" --author="user@example.com" 按作者过滤（例如邮箱）

git log --author=Caroline --since=2022-01-01 --until=2025-12-26 --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }'

git log --author=Soda --since=2022-01-01 --until=2025-12-26 --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }'
查询某段时间代码提交记录

git checkout -b dev --track origin/dev 创建本地分支dev,并关联到远程分支origin/dev

git  config core.ignorecase false  提交文件到仓库时不忽略大小写，即区分大小写
git  config core.ignorecase true  提交文件到仓库时忽略大小写，即不区分大小写