# Quick Start

- vim --version
- Open file browser => :Vex
- Close pane => C-w q
- Move through pane => C-w h/j/k/l
- Max pane => C-w o
- edit in column mode => C-v
- q => start/stop recording macro
- :py3 print('hello world')
- :echo join(split(&runtimepath, ','), "\n")
- :help 'textwidth'
- :ls => list all buffers, :b1 => switch to the first buffer, :bprev => previous buffer, :bnext => next buffer, :bd => delete buffer
- pip3 install --user --upgrade neovim
<https://shrydj.edu.sh.cn/views/register/>


# Roadmap

1. modes
2. text objects
3. actions
4. registers
5. macro
6. dot command
7. ex commands
8. regex
9. .vimrc
10. files
11. tabs & windows
12. plugins
13. scripts


# Basics

- Ctrl + r :: redo
- {/} :: block jump
- b :: back word
- insert mode, Ctrl + r :: insert register
- Ctrl + 6 :: switch between the latest two files
- Ctrl + a, Ctrl + x :: increment/decrement integer
- insert mode, Ctrl + v :: unicode input, like u2615 or 065


# FAQ

## Q: How to use text objects?

```
ciw, caw
cis, cas
cip, cap
cit, cat
ci(, ca(
ci[, ca[
ci{, ca{
ci', ca'
ci", ca"
```

## Q: How to open vimrc?

```
<Leader>vr
vim8 => ~/.vim
neovim => ~/.config/nvim
```

## Q: How to unquote a word?

- 'hello' => hello
- di'hPlxx
- surround.vim

## How do I explore files in vim?

See <https://shapeshed.com/vim-netrw/>.

## How do I edit my config file?

Neovim has the configuration file in ~/.config/nvim/init.vim  
You can use the following commands or hotkeys to open config file.  
```
:find $MYVIMRC
<SPC> vr
```

## How do I reload my config file without restarting vim?

```
:source $MYVIMRC
```

## How do I open files in vim?

```
:sp ~/tmp/fruit
:vs ~/tmp/fruit
:tabnew ~/tmp/fruit
```

## How do I use buffers?

```
:bp
:bn
:bd
<SPC> b
```

## How do I use tabs?

```
:tabnew
:tabp
:tabn
:tabclose
:tabonly
```

## How do I use panes?

```
Control + w q => close
Control + w h/j/k/l => move
Control + w o => max
```

## How do I search and replace?

```
:%s/foo/bar/gc  # c switch means to confirm before substitute.
```

## How do I go back to last place?

```
Ctrl-o: jump back to last place in jump list
Ctrl-i: opposite of Ctrl-o
```

## Q: How to use g command?

```
:g/^$/,/./-j => merge multiple blank lines
:g/<p>/normal @q => exectue macro in matched lines
```

## Q: How to use ex commands?

```
:'<,'>t0 :: Copy current highlight text to the start of the file.
:'<,'>m$ :: Move current highlight text to the end of the file.
:'<,'>normal A; :: Add semicolon to the end of every line of the current highlight text.
Ctrl + d :: Auto completion in ex commands.
@: :: Repeat last ex command.
:! :: Run shell command.
Ctrl + r + Ctrl + w :: In command mode, copy current word into the command.
```

## Q: How to refresh file content?

:e

## Q: How to check the setting value?

:set number?
:set tabstop?

## Q: How to close buffer?

:bd

## Q: How to record macro?

q => start recording.
q => stop recording.
@x => execute macro x.

## Q: How to open file browser?

:Vex => open pane
C-w q => close pane

## Q: How to find help?

```
:help g;
:help x
:help v_u
:help i_<Esc>
:help :quit
:help 'textwidth'
:help /[
:help help
:help ctrl-t
:help text // use ctrl-d to autocomplete

ctrl-] jump to subject
ctrl-t/ctrl-o jump back/forward
```

## Q: How to show all key bindings?

:map
:nmap g => all key bindings started with g
:verbose nnoremap

## Q: How to test color theme?

:source $VIMRUNTIME/syntax/hitest.vim

## Q: How to do the color theme?

red
green
blue
yellow
magenta
cyan
orange => bright red
purple => bright magenta

## Q: How to do keybindings?

http://vim.wikia.com/wiki/Mapping_keys_in_Vim_-_Tutorial_(Part_1)

## Q: How many modes in vim?

normal
insert
visual
command-line
replace
select
operator-pending

## Q: How to enter select mode?

gh

## Q: What is the select mode used for?
Select mode is used mainly for snippet plugins which highlight the current placeholder waiting
user to type some character to replace what was in the placeholder with just a single key.

## Q: How to check one key mapping?

:map <C-h>

:help map-listing
n => normal
v => visual or select
s => select
x => visual
o => operator pending
i => insert
! => insert or command
c => command

 * => not remappable
 @ => buffer local mapping
 & => script local mapping can be remappable

## Q: How to quickly open a new buffer?

:ene => open a new unamed buffer

## Q: How to open quickfix or location window?

:cw => open quickfix window
:lw => open location window

## Q: How to find out all the keycodes?

:help keycodes

<C-H> => <BS> => backspace
<C-I> => <Tab> => tab
<C-J> => <NL> => newline
<CR> => <C-M> => carriage return
<Esc> => <C-[>
<Space>
<F1>

## Q: How to convert all existing tabs into spaces?

:set expandtab
:retab

## Q: How to copy current file name or full path?

% => current file name in register
\# => alternate file name in register
:echo expand('%:p')

http://vim.wikia.com/wiki/Get_the_name_of_the_current_file

## Q: How to find tech info about the current file?

g C-g

## Q: How to format json?

<Leader>= -> Neoformat
:%!python -m json.tool

## Q: How to move the cursor after the pasted text?

gp
gP

## Q: How to show unicode of current position?

ga

## Q: How to build vim from source with clipboard and python3 support?
sudo yum remove vim
sudo yum remove vim-minimal
sudo yum install python36 python36-dev
git clone git@github.com:vim/vim.git
./configure --with-features=huge --enable-multibyte --enable-cscope --enable-gui=auto --with-x --disable-pythoninterp --enable-python3interp --with-python3-config-dir=/usr/lib64/python3.6/config-3.6m-x86_64-linux-gnu --enable-fail-if-missing
./configure \
--with-features=huge \
--enable-multibyte \
--enable-cscope \
--enable-gui=auto \
--with-x \
--enable-python3interp \
--with-python3-config-dir=/usr/lib/python3.5/config-3.5m-x86_64-linux-gnu \
--enable-fontset \
--enable-largefile \
--with-compiledby="huanghao <herbage_h2h@sina.com>" \
--enable-fail-if-missing
make distclean
make
sudo make install

## Q: How to move between code block?

[{ -> start of {
]} -> end of }
[( -> start of (
]) -> end of )
][ -> end of function
[[ -> start of function

## Q: How to use tabs?

:tabedit file1
gt/gT => navigate
:tabfirst/:tablast/:tabp/:tabn
:tabclose
:tabonly

## Q: How to use netrw?

```
:Vex => Split netrw vertically.
:Sex => Split netrw horizontally.
:Explore => open netrw
```

+ i :: Cycle through the view types.
+ I :: Toggle banner.
+ P :: Open file in previous pane.
+ % :: New file.
+ - :: Up one level.
+ d :: Make a new directory.
+ D :: Delete file.
+ gn :: make the directory under the cursor the top of the tree
+ gh :: hide/unhide dotfiles.

```
let g:netrw_liststyle = 1 "Default long view, showing file size and time stamp.
let g:netrw_banner = 0 "Hide banner.
let g:netrw_winsize = 25 "Set width to 25% of the page.
```

See "How to split window" to check operations about how to close netrw panes.

## Q: How to use filetype?

:set ft=html
:set filetype=javascript
:set filetype=html
:set filetype=css

## Q: How to use fold?

zf'b - make fold to register b
:5,16fo - make fold between 5 and 16
zc - close
zo - open
za - toggle
zj/zk - move between folds

## Q: How to use ctags?

C-]/C-w ]
g] - list all match
C-t/:tag
:tag xx - return to upper stack point
:tags - list stack
:tp/:tn/:tf/:tl
:ts

## Q: How to use abbreviation?

:ab => list
:ab ;jls java.lang.String
:una jls
:abc => remove all abbreviation
while in insert mode, just type ;jls then space, jls will expand to java.lang.String automatically. If you don't want to auto expand, just type C-v then space.
in vimscript: iabbrev mymail herbage_h2h@sina.com

## Q: How to jump to the start or end of a code block?

[{
]}
[(
])

## Q: How to echo the existing setting?

:set nocompatible?
:set

## Q: How to set encoding in vimrc?

set encoding=utf-8
set termencoding=utf-8
set fileencoding=utf-8,gbk

## Q: How to see if vim supports system clipboard?

vim --version | grep "clipboard"
if the result has minus like '-clipboard', then vim doesn't support system clipboard.

## Q: How to stop auto indent when paste from remote?

:set paste
after pasting, :set nopaste

## Q: How to jump to specific row or column?

:8 or 8G -> jump to row 8
6| -> jump to column 6
8G6| or :norm 8G6| -> jump to row 8 and column 6

## Q: Hot to use registers?

```
normal mode: "0p
insert mode: C-r0
command mode: let @a='C-ra' | let @2=@_
:reg => list all registers

"" => last cut text, unname register
"0 => last copied text, number register
"a => name register or macro
"% => current file, read-only register
": => last ex command, read-only register
". => last edit command, read-only register
"# => alternative file
"= => expression register
"_ => black hole register
"* => X11 clipboard
"+ => system clipboard
"/ => last search text
```

## Q: How to save readonly file?

Use command :w !sudo tee %

## Q: How to copy to system clipboard while in mac terminal mode which "+y register doesen't work?

add in .vimrc
vnoremap <silent> <C-c> :<CR>:let @a=@" \| execute "normal! vgvy" \| let res=system("pbcopy", @") \| let @"=@a<CR>

:w ! pbcopy
open TextEdit and Command+v

## Q: How to highlight the source file accoring to its grammer?

:syntax on
or
:set syntax=lisp

## Q: How to trim the special character '\r'?

:%s/\r//g

## Q: How to trim the ending space?

:%s/ *$//

## Q: How to delete all empty lines?

:g/^$/d

## Q: How to merge multiple empty lines into one?

:g/^$/,/./-j

## Q: How to remove all lines that don't match "www.example.com"?

:g!/www\.example\.com/d
:v/www\.example\.com/d

## Q: How to delete the current line and the following line at the same time?

2D or dj

## Q: How to convert upper or lower case?

guX to lowercase, gUX to uppercase.

## Q: How to open multiple files?

+ vim $file1
+ :split $file2/ :sp $file2 / :vs $file2, C-w C-w/C-w hjkl to switch between files.
+ Or :e $file2, :bp/:bn/:b $file1/:b# to switch, :bw to close the current buffer.
+ Or vim -o $file1 $file2 ... to open multiple files at the same time.
+ Or :tabe $file2 to open, :tabn/:tabp to switch, gt/gT can also switch.

## Q: How to see the current list of buffers?

 :ls

## Q: How to configure the indentation

+ set autoindent
+ set tabstop=4
+ set softtabstop=4
+ set shiftwidth=4
+ set expandtab

## Q: How to quote the current word using single quote?

+ ciw'C-r"'
+ ciw -> delete the current word
+ ' -> simple input single quote
+ C-r" -> insert the content of " register, aka the last delete
+ ' -> another single quote
----------
+ cw'C-rC-o"'
+ C-rC-o -> make the current word into the unname(") register so that dot(.) command can work on the other words.

## Q: How to use gn motion command?

- use regex to select.
- use cgn or alike to edit text.
- use . to repeat the changes to all matching text.

## Q: How to edit in column mode?

C-v enter column mode.
Press I or A to insert some text.
Esc then see all lines changed.

## Q: How to input special character?

in insert mode, C-v u2192 to type special character such as →.

## Q: How to move to the other end while in selection mode?

in visual mode, just press o.
:help v_o.

## Q: How to show line number?

:set number
:set relativenumber

## Q: How to count the occurence of some regex?

:%s/regex//gn

## Q: How to auto complete a line?

c-x c-l

## Q: How to reference current word in command mode?

/C-rC-w

## Q: How to indent a brace block?

:g/{/ .+1,/}/-1=
+ g/{pattern}/{command} -> for all lines that match pattern, execute command
+ /{/ -> lines that match {
+ .+1 -> current line plus one line downward
+ /}/-1 -> one line upward of lines that match }

## Q: How to exchange adacent char?

xp

## Q: How to add shell command output in the current file?

:r!date
:read !ls -al
:read !grep vim history.txt

## Q: The most important tips?

+ repeat dot(.) command

## Q: Any sites suggested to learn vim?

http://vim.wikia.com/
http://vimgolf.net/

## Q: Operations about jumplist and changelist?

```
C-o: older jump
C-i: newer jump
:jumps -> list jumps

g; -> older edit
g, -> newer edit
:changes -> list changes

ma -> setting mark a
'a -> jump to line of mark a
`a => jump to mark a
[(, ]) -> jump to the beginning/end
```

## Q: The sequence to clean a download page?

  A: 1. select all -> untabify
     1. :%s/ *$//

## Q: Any other tips?

+ /joe/e :: Set the cursor at the end of the match.
+ 3/joe :: Find 3rd joe.
+ /joe/e+1 :: Set the cursor at the end of the match plus 1.
+ /joe/s-2 :: Set the cursor at the start of the match minus 2.
+ /joe/+3 :: Set the cursor at 3 lines down.
+ /begin\_.*end :: Search for over multiple lines.
+ /fred\_s*joe :: Search for fred followed by any space (including new line) and joe.
+ /fred\|joe :: Search for fred or joe.
+ /\<fred\> :: Search for just fred, no more or less.
+ /.*fred\&.*joe :: Search for fred and joe in any order.
+ C-g :: Show the current file name and position.
+ g; g, :: Move backward/forward in change list.
+ g_ :: Jump to the last non-blank character in the line.

## Q: freq command in insert mode?

- c-h => back delete a char
- c-w => back detele a word
- c-u => back delete to line start
- c-r => insert register
- c-t => tab
- c-d => shift tab
- c-a => last inserted text
- c-v => insert special character
- c-p => completion forward
- c-n => completion backward
- c-x c-] => tag completion
- c-x c-f => filename completion

## Q: How to split window?

:vsp => vertical split
:sp => horizontal split
C-w h/j/k/l => navigate through split
C-w q => close current split window
C-w o => maximize current window
C-w +/-/</> => adjust split size
C-w = => reset split size
C-w | / _ => maximize split
C-w x => swap window
C-w w => cycle

## Q: How to reload the current file?

:e
set autoread

## Q: How to check python3 support?

:echo has("python3")
vim --version

## Q: How to install python3 provider for neovim?

pip3 install --user --upgrade neovim

## Q: How to search and replace or regex?

```
:%s/foo/bar/g
:'<,'>s/foo/bar/g
:5,9s/foo/bar/g
:%s/"value": "\/\w\+"/"value": ""/g :: "value": "/jrfc" => "value": ""
:%s/\d\{4}/bar/g
:%s/\d\+/bar/g
:%s/foo\s*/bar/g
:%s/\(foo \)1/\13/g :: foo 1 => foo 3
:%s/foo \zs\d\ze/3/g :: foo 1 => foo 3
:%s/foo\|apple/bar/g
:%s/\v(:.*;)(.*$\n) :: \v means very magic.
:%s/\v^(#+ .*)/\1\r :: Add an new line after #heading in markdown document.
:%s/\v(:.*;)(.*$\n):.*;\2/\1\2/g :: Remove duplicate lines like :xxxxx;cat in the log file.
:%s/\v\zs^(#.*)\ze\n[^\s]/\1\r/ :: Add an new line after #heading that didn't follow an new line in markdown document.
```

+ :range s/pattern/string/cgiI => i flag means ignore case. c flag means confirmation.

Grouping, Quantifiers, Meta Character, Alternation, Character Range, Greedy or Non-Greedy

```
 /\v\.: find the character '.'
 /\<i\>: find the word i.
 [vV]i: vi or Vi.
 ^vi$: only vi in the line.
 \s: white space
 \d: digit
 \w: word
 \+: 1 or more
 \=: 0 or 1
 \{n,m}: n to m
 *: 0 or more
 \{-}: non greedy
\(\) => group
\0 => whole matched pattern
\1 => group 1
\| => alternation, not greedy
\zs, \ze => just replace whatever between zs and ze.
```

```
".\{-}": match first word inside qutoe.
:s/.{-}/_g => match 0 character and substitute it to _
[0-9a-zA-Z] => character range
[^A-Z] => not uppercase letter
"[^"]\+ => quote words
[-0-9] => include -
[123^4] => include ^

\m: magic, default
\v: very magic => all characters except a-zA-Z_ has special meaning
\M: nonmagic
\V: very nonmagic
\c: case insensitive
\C: case sensitive
```


# Plugins

## nerdtree

o => open
go => open preview

## ctrlp

git@github.com:ctrlpvim/ctrlp.vim.git
:CtrlP
:CtrlPBuffer
:CtrlPMRU
C-j/C-k => navigate
C-r => toggle regex mode
C-d => toggle file name mode
C-n/C-p => history prompt

## vundle

### install with neovim

```
git clone https://github.com/VundleVim/Vundle.vim.git ~/.config/nvim/bundle/Vundle.vim
```

Add following script in your .vimrc file.
```
" plugin manager
filetype off
set rtp+=~/.config/nvim/bundle/Vundle.vim
call vundle#begin()

Plugin 'VundleVim/Vundle.vim' 
Plugin 'chriskempson/base16-vim'
Plugin 'ctrlpvim/ctrlp.vim'
Plugin 'tpope/vim-surround'
Plugin 'mg979/vim-visual-multi'

call vundle#end() 
filetype plugin indent on
```

```
:source %
:PluginInstall
:PluginUpdate
:PluginClean
```

## vim-surround

cs'"
cs"<q>
cst"
ds"
ysiw]
cs]{
yss) => wrap entire line with ()
first V, then S<p class="important">

## fzf

:Files
:Buffers

## Neoformat

:Neoformat
uncrustify -q -l JAVA ~/code/java/myjava/com/herb/Hello.java -c ~/.uncrustify/java.cfg --no-backup

## auto-pairs

()hello, <M-e> quickly move paren to the end of the word. => Fast Wrap
<M-p> toggle disable/enable
C-v( in insert mode will not trigger the plugin.

## UltiSnips

:UltiSnipsEdit
tab => trigger

C-j/k => next/previous placeholder

---java---
pa => package
cl => class
main => public static void main
p => System.out.println

---js---
:, => name: value

---snippet---
snippet hello "demo snippet" b => b means beginning of line
<${1:div}>
  `pwd`
  `!v xxxx `
  `!p xxxx `
</${1/(\w+).*/$1/g}>
endsnippet

---video---
UltiSnips cast in youtube

## Denite

:help Denite
:Denite buffer
:Denite file_rec
:Denite -input=foo file_rec

## neovim
sudo zypper in Neovim
sudo zypper in python3-neovim

chmod u+x nvim.appimage
./nvim.appimage

## neomake

:Neomake
:lwindow/:lprev/:lnext/:lopen/C-w q

## vim-javacomplete2

<leader>jI => JavaComplete-Imports-AddMissing
<leader>jA => JavaComplete-Generate-Accessors
<leader>jts => JavaComplete-Generate-ToString
<leader>jeq => JavaComplete-Generate-EqualsAndHashCode
<leader>jM => JavaComplete-Generate-AbstractMethods
C-x C-o => omni complete, C-n/p => next/previous
:JCimportsAddMissing

## vim-easymotion
\\w

## tcomment_vim

gcc => toggle current line
gc{motion}

## vim-fugitive

:Gstatus
- => stage/unstage
U => checkout
D => diff
[c/]c => prev chagne/next change
do/dp => diff obtain=submit/diff put=reset

## vim-yankstack

:Yanks

## vim-indentwise

 ```
[- => lesser level indent
[= => same level indent
[+ => greater level indent
[% => begining of block
0[_ => absolute level indent
```

## base16-vim

https://github.com/chriskempson/base16-vim

need first install base16-shell
https://github.com/chriskempson/base16-shell

## minpac

:call minpac#update()
:call minpac#clean()
:call minpac#add('tpope/vim-unimpaired')

## vim-visual-multi

+ Ctrl + <Up>, Ctrl + <Down> :: Add vertical cursors. This is in cursor mode.
+ Ctrl + n :: Add next word cursor. Use shift arrow to adjust selected characters. This is in extend mode.
+ <Tab> :: While in multi cursor status, change to visual mode. Switch between cursor mode and extend mode.
 
## vim-markdown

+ Plugin 'preservim/vim-markdown'
+ zr :: Open folds by one level.
+ zm :: Close folds by one level.
+ zR :: Open all folds.
+ zM :: Fold everything.
+ za :: Open a fold.
+ zc :: Close a fold.
+ zA :: Open a fold recursively.
+ zC :: Close a fold recursively.


# Scripts

## Variable scope

g: => global
s: => script
b: => buffer
w: => window
t: => tag
l: => function
a: => argument

## Useful expressions

expand('%:p') => the full path of the current file
line('.') => current line no
col('.') => current column no
:call cursor(1,1) => jump to line 1, column 1
&ft => current filetype
getpos('.') => current posistion
has('python') => check python support
echo join(split(&runtimepath, ','), "\n") => print all runtime path

## Vim functions must start with a capital letter if they are unscoped.

## echo/echomsg 'foo'

## 'hello' . 'world'

## pathogen#infect => load autoload/pathogen.vim/infect function

## function! means override

## let line = getline('.')

## let pos = col('.') - 1

## let before = strpart(line, 0, pos)

## line('.') => 2

## matchstr('  hello', '\s*\zs.') => 'h'

## stridx('hello', 'e') => 1

## 'hello'[1] => 'e'

## split('hello', '\zs') => ['h', 'e', 'l', 'l', 'o']

## repeat('h', 5) => 'hhhhh'

## substitue('Hi Mary', 'Mary', 'Judy', 'g') => 'Hi Judy'

   substitue('[apple]', '\v[\[\]]', '\\&', 'g') => '\[apple\]'

## get(['a', 'b'], 0, 'x') => 'a' while 'x' is the default value

## has_key(b:AutoPairs, a:key)

## for

for [open, close] in items(b:AutoPairs)
  let b:AutoPairsClosedPairs[close] = open
endfor

## if

if g:AutoPairsMapBS
  execute 'inoremap <buffer> <silent> <BS> <C-R>=AutoPairsDelete()<CR>'
endif

## Commands

### echo

echo "Hello, world!"

### echom

echom "Hello, world!"

### set
set number
set nonumber
set number!
set number?
set tabstop=4
set wrap
setlocal nowrap

### noremap

noremap q: :q
inoremap jk <Esc>
nnoremap <M-j> mz:m+<CR>`z
nnoremap <buffer> <Leader>x dd

### iabbrev

iabbrev adn and


# Third-party

## uncrustify

config file: ~/.uncrustify/java.cfg
force means first remove then add
sp_sparen_brace=force
input_tab_size=4
output_tab_size=4
indent_columns=4
indent_with_tabs=2
sp_template_angle=remove

## ctags

ctags --version
ctags -R .
ctags -R -f ./.git/tags .


# Article

## Vim Regular Expressions 101

http://vimregex.com/#substitute

## How does :g/^$/,/./-j (reduce multiple blank lines to a single blank) work in vim?

https://stackoverflow.com/questions/3032030/how-does-g-j-reduce-multiple-blank-lines-to-a-single-blank-work-in-vi

## Learn Vimscript the Hard Way - Steve Losh

## A Good Vimrc

https://dougblack.io/words/a-good-vimrc.html


# People

## Tim Pope

## Junegunn Choi

## Worp

## Steve Losh

## Chris Toomey

## Martin Grenfell

## Shougo


# Python3 support

:python3 print("Hello World!")


# Resource

Vim Awesome https://vimawesome.com


# Neovim

:checkhealth
pip3 install --user --upgrade neovim
~/.config/nvim/init.vim
