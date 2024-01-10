### 基础命令

git add *

git pull

git fetch

git commit -m 'init'

git statsh

git stash pop

git branch

git branch -a

git checkout master

git checkout -b release-1.2.1

git push -u

git log --author=Caroline --since=2023-01-01 --until=2023-12-26 --pretty=tformat: --numstat | awk '{ add += $1; subs += $2; loc += $1 - $2 } END { printf "added lines: %s, removed lines: %s, total lines: %s\n", add, subs, loc }'
查询某段时间代码提交记录