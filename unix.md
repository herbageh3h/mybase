# Quick Start

```
uname -a
lsb_release -a
groupadd hw3a
useradd jeff -m -g hw3a -s /bin/zsh => -m means to create home directory
passwd jeff
ssh-keygen
ssh-copy-id -i ~/.ssh/id_rsa.pub jeff@
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


