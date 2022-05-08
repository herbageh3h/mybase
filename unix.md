# Quick Start

```
uname -a
lsb_release -a
groupadd hw3a
useradd jeff -m -g hw3a -s /bin/zsh => -m means to create home directory
passwd jeff
add sudo to jeff
ssh-keygen
ssh-copy-id -i ~/.ssh/id_rsa.pub jeff@ocean001
sudo apt-get install zsh
sudo apt-get install rsync
install oh-my-zsh fasd, fzf, fd, ripgrep, tree
```

# Commands

## ln

```
ln -s /tmp/ ./abc :: Create a soft link "abc" poingting to "/tmp" directory.
ln -sf /usr/bin/python36 python :: -f means to update link.
ln schedule /datafs/bims :: Create link "/datafs/bims" pointing to "schedule" executable.
To delete link, just use "rm" command.
Only a soft link can refer to a directory while a hard link can not. 
```

## base64

echo msm | base64
eecho bXNtCg== | base64 -d

## ssh

```
ssh ocean001 => You can ignore username when your local machine user name is equal to remote user name.
ssh root@ocean001
ssh-copy-id -i ~/.ssh/id_rsa.pub huanghao@ali001
```

## mkdir

```
mkdir -p zsh_demo/{data,calculations}/africa/{kenya,malawi}/ zhs_demo/{data,calculations}/europe/{malta,poland}/ zsh_demo/{data,calculations}/asia/{nepal,laos}
```

## ln :: Create links.

```
ln -s /tmp/ ./abc :: Create a soft link "abc" poingting to "/tmp" directory.
ln -sf /usr/bin/python36 python :: -f means to update link.
ln schedule /datafs/bims :: Create link "/datafs/bims" pointing to "schedule" executable.
```
To delete link, just use "rm" command.

Only a soft link can refer to a directory while a hard link can not. 

## chown

```
chown -R oracle:dba /user1/oradata
```

## tar

```
tar -xvzf <tar_name:Python-3.6.0.tgz>
tar -cvf all.tar 1.txt 2.txt
sudo tar -xzf go1.10.1.linux-amd64.tar.gz -C /usr/local
tar -cvfz easyio.tar.gz conf/ ecosystem.json main.js package.json public/ yarn.lock
tar -tvf all.tar
sudo tar -zxvf apache-tomcat-8.0.33.tar.gz -C /opt/tomcat --strip-components=1
tar -xvf easyio.tar.gz -C easyio => must mkdir easyio
tar -xvPf docker.tgz
```

# Ohmyzsh

## install

see github homepage [ohmyzsh/ohmyzsh](https://github.com/ohmyzsh/ohmyzsh)


# Digital Ocean

+ [initial server setup](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-20-04#introduction)
+ [install docker](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)
```
ufw allow 3000 :: Allow port 3000 to be listened.
```

# Ubuntu

```
apt-cache search nodejs
sudo apt install nodejs
sudo apt install npm
```

# FAQ

## How to list all files under one directory in zsh?

```
print -l **/*
```

## How to get the size of a directory?

```
du -sh mydir
```

## How to add sudo to a user?

Configuration file is /etc/sudoers.

use visudo to edit the configuration file.

add script 'herb ALL=(ALL) ALL' to configuration file.

## How to change a user's login shell?

```
chsh -s /bin/zsh jeff
```

## How to generate ssh key?

```
ssh-keygen -t rsa -b 4096 -C "herbage_h2h@sina.com"
```

## How to use usermod?

```
usermod -d /home/herb herb => Set user home directory.
usermod -s /bin/zsh herb => Set user default login shell.
usermod -aG mygroup herb => Add user to some group.
```

## How to use rsync?

```
rsync -av /local/dir1/ /local/dir2/ => ensure files in /local/dir1 must also be in /local/dir2
rsync -av --delete /local/dir1/ /local/dir2/ => ensure two directories are totally identical
rsync -av --delete /local/dir1/ user@remote:/remote/dir2/ => sync between local and remote machine using ssh
rsync -vrh . root@ocean001:/data/backup
rsync -avzhe ssh --relative --omit-dir-times --progress ./ docker@$(docker-machine ip default):$(pwd)
```

## How to detect how many ports opened in one site?

Use nmap.
```
nmap <147.182.238.49:ip>
```

## How to use fasd?

fasd is a tool used to quickly jump to recent files and folders.

+ f :: file
+ a :: file or directory
+ s :: select
+ d :: directory
+ z :: cd with default
+ zz :: cd with interactive selection
+ , :: file & directory complete

```
cp `f molokai` ./    "Copy most recent molokai.vim into current folder.

f java$ => list recent .java files
fasd -A / fasd -D => add or delete paths

f,md    "file complete
d,base    "directory complete
climb,,f => tab completion for file starts with climb

C-r => command history search
C-t => fuzzy find through the current directory
tab => select current row
```

## How to use fzf?

trigger command
```
C-t => trigger
C-r => history fuzzy find
Esc => quit
Enter => select
fzf -m => multi select
tab => select (multi mode)
fzf -e => exact match
** => trigger
echo 'red\ngreen\nblue' | fzf
printenv | fzf
```

action shortcut during search
```
C-a :: Move to begin.
C-e :: Move to end.
C-f :: Move to right.
C-b :: Move to left.
C-k :: Move upward.
C-j :: Move downward.
C-p :: Move upward.
C-n :: Move downward.
```

command option
```
fzf -m :: -m means multiple. Hit <tab> to select or unselect.
fzf --cycle :: Option can iterate from begin to end and go to begin again.
```

search string tip
```
'home :: Use ' to restrict fuzzy search using the exact word.
md$|org$ :: Use | to represent 'or' operator.
!.git :: Use ! to negate search.
```

## How to use fd?

fd is an alternative to find.
```
sudo apt-get install fd-find
ln -s $(which fdfind) ~/.local/bin/fd
export PATH='/home/jeff/.local/bin:$PATH'
```

```
fd -h    "help
fd -V    "version
fd mail
fd '^N.*java$'
fd NotesMailManager.java /data/proj => search under certain root directory
fd => list all files under current directory flattern
fd -e java => list all .java files
fd -e java Date => list all .java files containing word 'Date'
fd -H => search hidden directory and file
fd -I => no ignore mode, search includes .git directory
fd -H -E .git => include hidden files, but exclude .git directory
fd -0 -e java | xargs -0 wc -l => -0 means to use null as separator instead of newline
```

## How to use ripgrep?

```
rg -w 4200 -g '!node_modules' :: search just the word 4200
rg -e 'Map<[^=>]*Map[^=>]*>' :: search Map<String, Map<String, String>>
rg -g '*.js' -w import :: search in all js file
rg foo -g '!*.min.js' :: search foo, exclude all *.min.js
rg foo :: simple search
rg -i foo :: search ignore case.
rg -e '\b4200\b' :: search just the word 4200
pt -Gjsp bin2 :: search only jsp files.
pt /G jsp bin2 :: search only jsp files on windows.
pt /c bin2 :: count the match places in each file.
pt /w bin2 :: match exactly bin2, not bin2xyz.
pt /l bin2 :: just print file names that contains bin2.
ag --jsp bin2 :: search jsp source files for bin2.
pt -g test.jsp :: search filename not content.
pt bin2 . :: under cygwin, you have to add the search directory in the end.
pt /ignore:*.sql bin2 :: Ignore *.sql in windows.
pt --ignore='*.sql' bin2 . :: Ignore *.sql in cygwin.
```

## How to use zypper?

```
zypper search --installed-only
zypper lr --url
sudo zypper ar -t yast2 -n 'sles12sp3' nfs://122.16.125.112/iso/sles12sp3 sles12sp3
sudo zypper ar http://122.18.29.171/sles/SLES-11-SP4-DVD-x86_6412211/ suse11sp4
sudo zypper ar /media local
sudo zypper install findutils-locate
sudo zypper install libtool autoconf automake cmake gcc-c++ gettext-tools
sudo zypper rr cd-521cc7ed
sudo zypper rm docker
sudo zypper search -s docker => list package version and repo
zypper se libnl
```

## How to install python 3.6?

```
tar -xvzf Python-3.6.0.tgz
cd Python-3.6.0
./configure --prefix=/usr/local/python3
make & make install
export PATH=/usr/local/python3/bin:$PATH
```

## How to install rpm?

```
rpm -qa | grep yast2-kdump
rpm -qp --requires w3m-0.5.3-38.git20180125.fc28.src.rpm
sudo rpm -ivh xsel-1.2.0-31.1.x86_64.rpm
sudo rpm -Uvh ansible-*.noarch.rpm
sudo rpm -ivh xsel-1.2.0-31.1.x86_64.rpm --nodeps => ignore dependency
rpm -ql w3m-img
```

## How to use locate command?

```
- updatedb
- locate locate.db => Search through path and file name.
- locate -b foo => Just match file name, not including path.
- locate -b '\foo' => Exact match file name.
- locate '*/rulesets'
```
