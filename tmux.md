# QuickStart

```
tmux ls
tmux new -s hello
tmux a -t hello
Control + b d => detach
Control + b [ => copy mode
```

+ tmux new -s hello => new session
+ C-b d => leave the current session
+ tmux a -t hello => reopen session
+ C-b c => new window
+ C-b p/n => toggle window
+ C-b , => rename window
+ C-b % => split new pane in vertical
+ C-b " => split new pane in horizontal
+ C-b o => toggle pane
+ C-b x => close the current pane
+ C-b ? => list all commands
+ C-b z => toggle full screen
+ C-b & => kill window
+ C-b :swap-window -t 0 => swap current window with window 0 
+ C-b SPC => switch layout
+ C-b z => toggle fullscreen
+ C-b $ => rename session
+ C-b : => execute command
+ C-b ? => help
+ C-b . => change window to another nonexisted index


# Roadmap

1. session
2. window
3. pane


# FAQ

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

### C-b s :: List all sessions.

### C-b ( || C-b ) :: Previous/Next session.

### C-b w :: List all windows.

### C-b c :: Create window 

### C-b , :: Rename window

### C-b p/n :: previous/next window

### C-b & :: Close the current window.

### C-b % :: Split horizontally.

### C-b " :: Split vertically.

### C-b o :: Swith between panes.

### C-b x :: Close the current pane.

### C-b up/right/down/left arrow: Cycle through the panes.

### C-b SPC :: Switch layouts.

### C-b d :: Detach the current session.

### C-b q :: Display the pane number.

### C-b ? :: List all the hotkeys.

### C-b z :: Zoom in/out the pane, toggle full screen

### C-b [ :: Enter copy mode.

space -> start selecting text, enter -> end selecting text and copy into clipboard, C-b ] -> paste 

### C-b : => Execute command.

### C-b t => Big clock.

### C-b . => Move window to a new index

### C-b </> :: Swap pane

### C-b H/J/K/L :: Resize pane

### How to list all hotkeys?

tmux list-keys | less
C-b ?

### Configuration file: ~/.tmux.conf

### How to check the version :: tmux -V

### How to resize pane?

C-b :
resize-pane -D 2
-U=up, -D=down, -L=left, -R=right

### How to refresh configuration?

C-b :source-file ~/.tmux.conf
tmux source ~/.tmux.conf

### How to install tmux plugin manager?

git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
C-b I: install all plugins
C-b U: update all plugins

### How to customize themes?

jimeh/tmux-themepack

### How to execute command on all panes?

C-b :setw synchronise-panes

### How to toggle between pane and window?

C-b :joinp -s :1 => merge window 1 to current window
C-b :joinp -t :1 => join current pane to window 1
C-b :break-pane  => break current pane to another window

### How to swap pane?

C-b :swap-pane -U
C-b :swap-pane -t 1 => swap current pane and pane 1

### How to clear history?

bind-key u clear-history
