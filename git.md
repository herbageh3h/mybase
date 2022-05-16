# Quick Start

```
git init
git add .
git commit -m "create repo"
git remote add origin git@github.com:herbageh3h/mybase.git
git push -u origin master
git pull
git config --global --unset http.proxy
git branch -r
git checkout -b feature_2206A origin/feature_2206A
git clone
git log
git show
```


# Roadmap

+ working directory
+ staging area
+ git repository
+ branches and master
+ HEAD
+ tags
+ commits
+ trees and blobs


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
# 注意本地分支代码不一定是最新，需要使用 pull 的方式与远程仓库保持同步
# if xx is a remote branch and you don't have a local branch named xx, this command will help you create a new branch xx and track the remote branch xx automatically.
# git checkout 就是将版本库的文件覆盖到工作区
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

## git rm

```
git rm .idea/ -r             # Remove .idea direcotry from git but not from pyshic disk.
```

## git add

```
git add .
```

## git commit

将变动检入到本地仓库中
- git commit --amend :: 将本次提交合并到最近一次提交中，用本次提交的内容覆盖之前提交的内容。（之前提交未被覆盖的内容仍属于正常提交。）
- git commit --amend -m "updated commit message" :: update new commit message.
- git commit --amend --no-edit :: no need to update commit message, but merge new files.
- git commit -a :: To add and commit all the files to the repository, skipping add process.

## git merge

将 xxx 分支合并到当前分支中
- git merge --no-ff -m "merge with no-ff" dev :: 不采用 fast forward 方式合并 dev 分支，保留分支提交历史，合并时新做了一次 commit
- git merge --squash feature :: merge feature into master, but not commit. commit all changes in feature branch next time.

## git config :: git parameter setting

- git config --global user.name herbageh3h
- git config --global user.email herbageh2h@gmail.com
- git config --global push.default simple :: Since Git 2.0, git defaults to 'simple' behaviour, which only pushes the current branch to the remote branch.
- git config --global alias.co checkout :: 把 co 作为 checkout 的别名
- git config --global credential.helper cache :: save git user and password temporarily in cache so that you don't have to enter password every time you push.
- git config log.date iso :: 设定日志显示的时间格式为 2015-11-01 10:28:03 +800 这样的格式
- git config --list :: check current config.
- git config --get user.name :: Get specified configuration.
- git config --global credential.helper osxkeychain :: Cache password.
- git config --global core.autocrlf true :: set line ending. if on windows, set to true, which means client use \r\n while server use \n. if on mac or linux,
    set to input, which means client use \r\n or \n, but server just use \n.
- git config --global diff.tool vscode
- git config --global difftool.vscode.cmd "code --wait --diff $LOCAL $REMOTE"

## git init

- git init :: 在本地创建 git 代码仓库

## git status

- git status :: 查看当前版本库状态
- git status -s :: show simplified version of status.

## git diff

比较当前修改内容
- git diff :: check the difference between the work directory and the stage area.
- git diff HEAD -- xx.txt
- git diff xx_commit_id1 xx_commit_id2 :: check the difference between two commits.
- git diff --staged :: see what change will be in the next commit.
- git difftool :: use diff tool like vscode to see the difference.

## git reset

代码回退到之前的某个版本
- git reset                  # By default, use --mixed HEAD to reset, which means change commit tree and staging area back to HEAD commit but working directory not changed.
- git reset --hard           # hard means change commit tree and staging area as well as working directory.
- git reset --mixed          # mixed means change both commit tree and staging area.
- git reset --soft           # soft means only change commit tree
- git reset --hard HEAD^
- git reset --hard xx_commit_id 代码回退到某个 commit id 代表的版本状态。（commit id 可以用 git log 进行查看）
- git reset HEAD xx.txt  撤销暂存区的修改，回到和版本库一致的状态
- git reset --hard origin/master 将本地仓库回退到和远程仓库完全一致的状态，抛弃本地其他修改。
- git reset 可以将暂存区的内容回退，但不会直接将本地文件回退。使用 git reset 以后还需调用 git checkout -- xx_file_name 将本地文件回退到和暂
    存区中内容保持一致。
- git reset --hard 不同于 git reset，它会将所有的提交记录，本地文件，暂存区和本地仓库全部回退到之前的某个状态。

## git reflog

查看 git 操作的每一次纪录

## git rm

Remove files in both stage area and work directory.
- git rm file1.txt
- git rm --cached :: only remove from the stage area, keep it in the work directory.
- git rm --cached -r bin/ :: -r means recursively remove.

## git remote add origin git@github.com:herbageh3h/learngit.git

将本地仓库添加到 github 远程仓库
- git remote 查看远程版本库的情况
- git remote -v 查看更详细的远程版本库信息
- git remote show origin :: inspect remote repository(origin) for more information.
- git remote set-url origin git@github:herbageh/myorg.git :: change repository upstream url.
- git push --set-upstream origin/master

## git push -u origin master

- 格式： git push 远程主机 本地分支:远程分支
- 把本地库的所有内容推送到远程库上
- -u 绑定默认的远程主机
- git push origin master 把本地 master 分支推送到远程版本库的 master 分支上
- git push origin xx_tag_name 把标签推送到远程库
- git push origin --tags 把所有尚未推送到远程的标签全部推送到远程库
- git push origin :refs/tags/xx_tag_name 将本地删除的 xx_tag_name 推送到远程，将远程的对应标签进行删除操作
- git push origin :dev 删除远程仓库的 dev 分支，原理是用本地仓库的空白分支替换远程仓库的 dev 分支
- git push origin local_dev:origin_dev 在远程仓库上新建一个 origin_dev 分支，将本地 loacl_dev 的内容推送到新分支上

## git clone git@github.com:herbageh3h/myorg.git

- 将远程版本库的内容复制到本地
- git clone --depth 1 https://github.com/junegunn/fzf.git ~/.fzf
- git clone https://github.com/angular/quickstart.git angular001
- git clone --recursive https://github.com/junegunn/fzf.git

## git stash

- 把当前现场保存下来，等以后再进行恢复
- git stash list
- git stash apply 恢复到之前保存的现场
    + git stash apply stash@{0}
- git stash drop 删除最近一次的 stash
- git stash pop 恢复到最近一次的 stash 并删除对应的 stash

## git tag xx

- 打标签，xx 为标签名
- git tag xx 6224937 针对 commitid 为 6224937 的修改情况打标签
- git tag 列出标签列表
- git tag -a xx_tag_name -m "xx_tag_comment" xx_commit_id 多参数版，－a 表示标签名，－m 表示标签注释
- git tag -d xx_tag_name 删除某个标签
- git push --tags :: Push local tags to remote repo.

## git show

- git show xx_my_tag :: 显示标签名为 xx 的详细情
- git show xx_commit_id :: check what the commit do.
- git show HEAD~1 :: watch the commit immediately before head.
- git show xx_commit_id:xx_file_name :: watch the whole content of some file in the stage area.

## .gitignore

工作区中不需要纳入版本库的文件列表

<https://github.com/github/gitignor>

## .gitconfig

针对当前用户的 git 配置信息

## 如何利用 ssh 建立一个远程库？

- 登陆 github 建立一个远程库
- 在本地新建一个空目录作为本地库的根目录
- git init 创建一个本地库
- git remote add origin git@github.com:herbageh3h/hellojs.git
- 本地新建一个文件，通常是 Readme.md
- git add Readme.md
- git commit -m "init repo"
- 创建本地 ssh key, cd ~/.ssh, ssh-keygen, 提示内容都默认按回车
- ssh-keygen -t rsa -C "youremail@example.com"
- 生成 id_rsa 和 id_rsa.pub 作为私钥和公钥，将公钥的内容拷贝，在 github 中增加对应的 sshkey
- 在本地终端采用 ssh -T git@github.com 进行测试，看看 ssh 是否可以正常访问 github
- 到本地仓库中，git push -u origin master，将本地仓库推送到远程仓库并建立链接

## git fetch

- git fetch origin :: just download remote repo information to your repo, not updating your work directory.
- git fetch --all :: fetch all the information on the remote repository.

## git submodule

- git submodule add git@github.com:herbageh3h/myorg.git ~/data/org :: add some repo under current project.

## git submodule update --init --recursive :: add submodule recursively.
## git blame

- git blame xx_file :: find out who changed what and when in xx_file

## git grep

- git grep "hello" xx_my_commit :: Search through xx_my_commit to find which file contains hello.

## git cat-file

- git cat-file -t xx_commit_id :: To show the type of the xx commit id. The types include blob, tree, tag, commit.
- git cat-file blob xx_id :: To print the result of the file according to the blob id.

## git ls-tree

- git ls-tree xx_tree_id :: To list all the changed files in the xx tree id.

## git rebase

- To maintain topic branches.
- git rebase master :: put current branch on top of master, remain in current branch
- git rebase my_branch => merge my_branch on top of current branch
- git pull --rebase
- git add <some conflict resolved files>
- git rebase --continue
- git rebase --abort

## git mv

- Move files in the stage area as well as work directory.

## git ls-files

List files in the stage area.

```
git ls-files -s 
```

## git restore

- Recover file from repo or stage.
- git restore --source=HEAD~1 xx_file_name


# FAQ

## How to generate ssh key?

```
ssh-keygen -t rsa -C "youremail@example.com"
```

## Cannot checkout, file is unmerged. How to solve it?

```
git reset
git checkout -- <file.txt>
```

## How to remove all untracked local files?

git clean -fdx => Note this will remove all ignore files included in .gitignore. So better use -n for preview first.

## How to rollback local changes?

- git reset --hard origin/master
- git restore .
- git checkout HEAD -- src/main/java/com/icbc/ama/iais/IAISApplication.java

## How to switch back to master branch and keep all the work files synchronized with master?

git checkout master 
git reset --hard origin/master

## How to synchronized completely with remote repo?

git checkout {{another_branch}}
git branch -D {{target_branch}}
git checkout -b {{target_branch}} {{origin/target_branch}}

## How to reserve some local changes while commiting other changes?

```
git update-index --assume-unchanged *.xml
```

## How to get rid of the annoying message "LF will be replaced by CRLF in xx"?

git config --global core.autocrlf input
in windows: git config --global core.autocrlf true
in linux:   git config --global core.autocrlf input

## How to reverse git add result?

git reset <=> git add

## How to recover from git reset --hard

git fsck --lost-found
cd /data/proj/msms/.git/lost-found/other
FILES=*
COUNTER=0
for f in $FILES; do
  echo "Processing $f file..."
  git shwo $f > "/data/proj/msms/$COUNTER.m"
  let COUNTER=COUNTER+1
doner

## How to push a existing repo to remote?

git remote add origin git@github.com:herbageh3h/learngit.git
git push -u origin master

## How to do add and commit in one command?

git commit -am "xx_commit_msg"
git config --global alias.add-commit '!git add -A && git commit'

## How to unstage files?

- git restore --staged xx_file_name :: rollback changes in the stage area to the work directory.
- git restore xx_file_name :: rollback changes in the work directory.

## How to find out why it is slow in git?

GIT_TRACE=1 git push

## How to count commits per author?

```
git shortlog -sne :: count commits per author
-e flag display the author email
```

## How to solve merge conflicts?

First undo a merge.
```
git merge --abort
git reset --merge
```
