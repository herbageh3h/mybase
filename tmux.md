# Tmux
## Quick Start
```
tmux ls
tmux new -s hello
tmux a -t hello
Command + b d => detach
Command + b [ => copy mode
```

## FAQ
### 1. How do I rename a window and keep it unchanged automatically?
Use `Command + b ,` to rename your window.

Add `set -g allow-rename off` to your .tmux.conf file to keep the window name
unchanged automatically.

### 2. Where do I find my .tmux.conf file?
usually under your home directory, ie ~/.tmux.conf

you can also use `locate .tmux.conf` to find the dot file.

## Hotkey
- Command + b , => rename window
