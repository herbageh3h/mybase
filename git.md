# Quick Start
```
git init
git add .
git commit -m "create repo"
git remote add origin git@github.com:herbageh3h/mybase.git
git push -u origin master

git config --global --unset http.proxy

git branch -r
git checkout -b feature_2206A origin/feature_2206A
```


# Commands

## git branch

```
git branch --list    "查看当前分支
                     "注意这儿查看的分支都是本地仓库的分支
                     "分支前带星号表示该分支为当前分支
git branch -vv :: to see all the tracking branches you set up.
git branch -r :: Show remote tracking branches.
git branch --set-upstream dev origin/dev 把本地的 dev 分支与远程库的 dev 分支关联上
git branch -d xx
+ 删除 xx 分支
git branch -D xx 强行删除某个分支
git branch -a :: show remote branch 
```

## git checkout

```
git checkout -b dev origin/dev    "Checkout remote branch origin/dev into local branch dev. If local branch doesn't exist, create it.
git checkout tags/v2.4.3.0-1 :: 切换到具体标签
git checkout xx :: 切换到具体分支
+ 注意本地分支代码不一定是最新，需要使用 pull 的方式与远程仓库保持同步
+ if xx is a remote branch and you don't have a local branch named xx, this command will help you create a new branch xx and track the remote branch xx automatically.
+ git checkout 就是将版本库的文件覆盖到工作区
git checkout -b xx :: 新建 xx 分支并自动切换到该分支
git checkout -- xx.txt :: 撤销工作区的修改，回到和暂存区状态一致的内容
git chekcout . :: 撤销所有没提交的内容
```

## git log

```
git log --oneline --format=format:"%h %an %ci %s" :: %h => commit id short, %an => author, %ci => commit date, %s => subject
git log :: 查看本地仓库变动的历史
git log --oneline :: show quick log.
git log --oneline --reverse :: show the log reversely.
git log --oneline --stat :: show brief history with stat.
git log --pretty=oneline :: 用比较容易理解的形式展现日志
git log --graph --pretty=oneline --abbrev-commit :: 用图的方式展现日志，主要用于查看曾经做过合并冲突的内容
git log -g :: 查看所有变更的明细，包括 commit --amend, reset --hard 等(这些在 git log 中是看不到的)。
git log --since="2 weeks ago/9 months ago/2 years ago" :: Check commits from the last two weeks.
git log --diff-filter=D --summary :: List all delete history.
git diff-tree --no-commit-id --name-only -r bd61ad98 :: Show changed file list in one commit.
git log --abbrev-commit :: show commit id in 7 digit mode.
git log --date="short/iso" :: show date in yyyy-mm-dd format.
git log --all :: see all the branches submit.
git log -3 :: show latest 3 commits.
git log --oneline --author=kfzx-huanghao :: show one person's commits.
git log -p --follow xx_file_path :: show one file's history.
git log --grep="berry" :: show commits that contain the keyword berry
```

# FAQ

## How to generate ssh key?

```
ssh-keygen -t rsa -C "youremail@example.com"
```
