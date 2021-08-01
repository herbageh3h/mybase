# Vim

## Quick Start

## FAQ

### 1. How do I explore files in vim?

See <https://shapeshed.com/vim-netrw/>.

### 2. How do I edit my config file?

Neovim has the configuration file in ~/.config/nvim/init.vim  
You can use the following commands or hotkeys to open config file.  
```
:find $MYVIMRC
<SPC> vr
```

### 3. How do I reload my config file without restarting vim?

```
:source $MYVIMRC
```

### 4. How do I open files in vim?

```
:sp ~/tmp/fruit
:vs ~/tmp/fruit
:tabnew ~/tmp/fruit
```

### 5. How do I use buffers?

```
:bp
:bn
:bd
```

### 6. How do I use tabs?

```
:tabnew
:tabp
:tabn
:tabclose
:tabonly
```

### 7. How do I use panes?

```
Command + w q => close
Command + w h/j/k/l => move
Command + w o => max
```

## Hotkeys

## Netrw

```
:Vex
:Sex
```

* i: Cycle through the view types.
* I: Toggle banner.
* P: Open file in previous pane.
* %: New file.
* -: Up one level.
* d: Make a new directory.
* D: Delete file.

```
let g:netrw_liststyle = 1 "Default long view, showing file size and time stamp.
let g:netrw_banner = 0 "Hide banner.
let g:netrw_winsize = 25 "Set width to 25% of the page.
```
