# Tmux

## Quick Start

```
tmux -V
tmux new -s hello
tmux a -t hello
tmux ls
Ctrl-b d    "Detach.
Ctrl-b [    "Copy mode. Press 'q' to quit copy mode.
Ctrl-b x    "Close pane.
Ctrl-b :swap-window -t 0    "swap current window with window 0.
```


## Shortcuts

+ tmux new -s hello => new session
+ Ctrl-b d => leave the current session
+ tmux a -t hello => reopen session
+ Ctrl-b c => new window
+ Ctrl-b p/n => toggle window
+ Ctrl-b , => rename window
+ Ctrl-b % => split new pane in vertical
+ Ctrl-b " => split new pane in horizontal
+ Ctrl-b o => toggle pane
+ Ctrl-b x => close the current pane
+ Ctrl-b ? => list all commands
+ Ctrl-b z => toggle full screen
+ Ctrl-b & => kill window
+ Ctrl-b :swap-window -t 0 => swap current window with window 0 
+ Ctrl-b SPC => switch layout
+ Ctrl-b z => toggle fullscreen
+ Ctrl-b $ => rename session
+ Ctrl-b : => execute command
+ Ctrl-b ? => help
+ Ctrl-b . => change window to another nonexisted index


## Roadmap

1. session
2. window
3. pane


## FAQ

### How do I rename a window and keep it unchanged automatically?

Use `Command + b ,` to rename your window.

Add `set -g allow-rename off` to your .tmux.conf file to keep the window name
unchanged automatically.

### Where do I find my .tmux.conf file?

usually under your home directory, ie ~/.tmux.conf

you can also use `locate .tmux.conf` to find the dot file.

### How do I change window order?

```
swap-window -t -1 => swap window with its previous sibling
```

### How to create a new session?

tmux new -s hello

### How to list all the sessions?

tmux ls
tmux list-sessions

### How to close a session?

tmux kill-session -t hello

### How to close all session?

tmux kill-server
pkill tmux

### How to attach again?

tmux a -t hello
tmux attach
tmux attach -t hello

### Ctrl-b s :: List all sessions.

### Ctrl-b ( || Ctrl-b ) :: Previous/Next session.

### Ctrl-b w :: List all windows.

### Ctrl-b c :: Create window 

### Ctrl-b , :: Rename window

### Ctrl-b p/n :: previous/next window

### Ctrl-b & :: Close the current window.

### Ctrl-b % :: Split horizontally.

### Ctrl-b " :: Split vertically.

### Ctrl-b o :: Swith between panes.

### Ctrl-b x :: Close the current pane.

### Ctrl-b up/right/down/left arrow: Cycle through the panes.

### Ctrl-b SPC :: Switch layouts.

### Ctrl-b d :: Detach the current session.

### Ctrl-b q :: Display the pane number.

### Ctrl-b ? :: List all the hotkeys.

### Ctrl-b z :: Zoom in/out the pane, toggle full screen

### Ctrl-b [ :: Enter copy mode.

space -> start selecting text, enter -> end selecting text and copy into clipboard, Ctrl-b ] -> paste 

### Ctrl-b : => Execute command.

### Ctrl-b t => Big clock.

### Ctrl-b . => Move window to a new index

### Ctrl-b </> :: Swap pane

### Ctrl-b H/J/K/L :: Resize pane

### How to list all hotkeys?

tmux list-keys | less
Ctrl-b ?

### Configuration file: ~/.tmux.conf

### How to check the version :: tmux -V

### How to resize pane?

Ctrl-b :
resize-pane -D 2
-U=up, -D=down, -L=left, -R=right

### How to refresh configuration?

Ctrl-b :source-file ~/.tmux.conf
tmux source ~/.tmux.conf

### How to install tmux plugin manager?

git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
Ctrl-b I: install all plugins
Ctrl-b U: update all plugins

### How to customize themes?

jimeh/tmux-themepack

### How to execute command on all panes?

Ctrl-b :setw synchronise-panes

### How to toggle between pane and window?

Ctrl-b :joinp -s :1 => merge window 1 to current window
Ctrl-b :joinp -t :1 => join current pane to window 1
Ctrl-b :break-pane  => break current pane to another window

### How to swap pane?

Ctrl-b :swap-pane -U
Ctrl-b :swap-pane -t 1 => swap current pane and pane 1

### How to clear history?

bind-key u clear-history
