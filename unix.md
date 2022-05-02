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
install oh-my-zsh fasd, fzf, ctrlp, fpp, fd, ripgrep, tree
```

# Commands

## base64

echo msm | base64
eecho bXNtCg== | base64 -d

## ssh

```
ssh ocean001 => You can ignore username when your local machine user name is equal to remote user name.
ssh root@ocean001
ssh-copy-id -i ~/.ssh/id_rsa.pub huanghao@ali001
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

```
z => cd with default
zz => cd with interactive selection
cp `f molokai` ./ => copy most recent molokai.vim into current folder
f java$ => list recent .java files
fasd -A / fasd -D => add or delete paths
, => file & directory complete
f, => file complete
d, => directory complete

climb,,f => tab completion for file starts with climb

C-r => command history search
C-t => fuzzy find through the current directory
tab => select current row
 ** => trigger
```

# OHMYZSH

## install

see github homepage [ohmyzsh/ohmyzsh](https://github.com/ohmyzsh/ohmyzsh)


# DIGITAL OCEAN

+ [initial server setup](https://www.digitalocean.com/community/tutorials/initial-server-setup-with-ubuntu-20-04#introduction)
+ [install docker](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-20-04)
```
ufw allow 3000 :: Allow port 3000 to be listened.
```

# UBUNTU

```
apt-cache search nodejs
sudo apt install nodejs
sudo apt install npm
```
