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

## grep command

```bash
grep 'model name' /proc/cpuinfo
grep MemTotal /proc/meminfo
grep -l mango * => -l表示列出有匹配记录的文件清单，-L表示列出不含匹配记录的文件清单。
grep -R '/var/lib/docker' *.sh => -R means recursive search under the current directory
grep -n apple foo => -n means to print line number
grep -H apple foo => -H means to add filename to output
grep 'apple\|banana' foo
grep -E 'apple|banana' foo
grep -Fnr kgsp ./ => -F means only search the string, not regex.
grep -v hello test :: 搜索test文件中不包含hello的文本行
egrep 'hello|morning' test :: 搜索test文件中包含hello或者morning的文本行
grep vim history.txt -> find all lines that contains vim.
grep '' **/income.txt -> show the name of each file and its content.
grep '\<80\>' foo -> find words that is just 80, not 8080.
grep -o '\b[0-9]{5}\b' address.txt => Print numbers that look like US zip code, -o means only print the matching part.
```

## sed command

+ sed是在线编辑工具, sed先将文件的一行读入缓存区，然后对该行内容执行所有的命令，并将处理后的结果进行输出。
+ sed主要的功能包括打印、删除和替换。
+ sed 's/test/prod/g' file1 > file2 => 批量替换
+ sed '/^$/d' test => delete empty lines
+ sed -n '/test/p' test :: -n表示不打印任何文本行，p表示打印符合条件的行，这两个参数通常结合使用
+ sed '2d' test
+ sed -n '10p' foo => 打印第10行
+ sed '2,$d' test
+ sed '2,10!d' foo => 打印除第2行到第10行以外的行
+ sed '1~2p' foo => 打印基数行
+ sed '/test/d' test
+ sed -i 's/foo/bar/g' foo.txt => replace all foo to bar in foo.txt, -i means to write back to foo.txt.
+ sed 's/test/second &/' test :: &代表匹配到的文本内容
+ sed 's/\(es\)/\1s/' test :: \1代表括号匹配到的内容
+ sed -n '/afternoon/,/evening/p' test :: ,表示行范围
+ sed '/afternoon/,/evening/s/$/ end/' test :: 针对afternoon到evening之间的所有行，每行末尾增加' end'字符串
+ sed -e '1d' -e '1d' test :: 针对每一行同时执行多项命令
+ sed 's/foo/bar/g;s/apple/banana/g' fruit => 分号连接多个编辑命令
+ sed '/hello/r bye' test :: 在test文件的每一行包含hello的行下面添加bye文件的内容
+ sed '/afternoon/{n; s/hello/bye/;}' test :: n代表移动到下一行, 大括号代表一组命令
+ sed '1,$y/h/R/' test
+ sed -n '/^#/!p' /etc/passwd :: 打印passwd文件中不是以#开头的文本行
+ sed -i '1s/^\xef\xbb\xbf//' AllTest.java :: 将UTF-8(BOM)转换为UTF-8
+ sed -ire '\?^[[:space:] ]*DOCKER_HOME=? d' /etc/profile.local => -r means extended regular expression

## awk command

+ awk是文本分析工具
+ awk '{print $2}' /etc/passwd
+ awk -F: '/^root:/{print $1, $3, $6;}' /etc/passwd
+ awk -F: '{print $1}' source_file
+ awk '{print NF}' /etc/passwd
+ df -P | awk 'NR>2{sum += $2}END{print sum}' => NR>2 means calc from line number 2.
+ cat /etc/passwd | sed -n '/^#/!p' | awk -F: 'BEGIN {linum = 0;} {print linum,":",$1; linum = linum + 1;}'
+ ls -l /home | awk '{if (NR > 1) print $9}'
+ awk '/^color00=/,/^$/ {print}' base16-monakai.sh | sed 's/#.*//'
+ awk -F: '$3>=1000{printf("User:%-15sUID:%s\n", $1, $3);}' /etc/passwd => 第3个字段大于1000的才进行打印
+ cat 360.csv | awk -F',' '{if(length($1)==3) print $0}'
+ cat 3603.csv | awk -F',' '{if($2=="n") print $0}'

## find command

```
find . -name "*.sh"
find . -name .DS_Store -exec rm '{}' \; => quote {} Because the file path may contain space. Backslash ; because ; is special in shell.
find . -iname "*.bin" => ignore uppercase or lowercase
find * -type f
find . -type f -mtime +3 -mtime -4 => Find files that were modified over 3 days but not 4 days.
find . -type f -mtime 3 => Find files that were modified just 3 days before.
find . -type f/d/l => f:file, d:direcotry, l:link
find . -executable -type f => find all executable under current directory and not including children directory
find . -executable -type f -exec mv {} /data/app/redis/bin \;
find . -user foo -a \( -name '*.c' -o -name '*.h' \) -a -perm 644 -a -atime +8 => -a means and, -o means or
find . ! \( -name "*.sh" -o -name "*.txt" \)
```

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
echo bXNtCg== | base64 -d

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
