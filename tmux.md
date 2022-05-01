# Tmux

## Quick Start

```
tmux ls
tmux new -s hello
tmux a -t hello
Control + b d => detach
Control + b [ => copy mode
```

## FAQ

### 1. How do I rename a window and keep it unchanged automatically?

Use `Command + b ,` to rename your window.

Add `set -g allow-rename off` to your .tmux.conf file to keep the window name
unchanged automatically.

### 2. Where do I find my .tmux.conf file?

usually under your home directory, ie ~/.tmux.conf

you can also use `locate .tmux.conf` to find the dot file.

### 3. How do I change window order?

```
swap-window -t -1 => swap window with its previous sibling
```

## Hotkey

- Control + b , => rename window
- Control + b c => new window
- Control + b : => execute command
- Control + b ? => help
- Control + b . => change window to another nonexisted index
