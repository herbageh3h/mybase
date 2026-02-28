# Tmux

## Concepts

tmux has a three-level hierarchy:

```
Server
└── Session (named workspace, survives disconnects)
    └── Window (tab-like, full terminal view)
        └── Pane (split within a window)
```

The **prefix key** is `Ctrl-b` by default. Every shortcut starts with it.

---

## Installation

```bash
# macOS
brew install tmux

# Ubuntu/Debian
sudo apt install tmux

# Check version
tmux -V
```

---

## Sessions

### CLI

```bash
tmux                        # new unnamed session
tmux new -s work            # new session named "work"
tmux ls                     # list sessions
tmux attach                 # attach to last session
tmux attach -t work         # attach to "work"
tmux kill-session -t work   # kill session
tmux kill-server            # kill all sessions
tmux rename-session -t old new  # rename session
```

### Inside tmux

| Key | Action |
|-----|--------|
| `Ctrl-b d` | Detach from session |
| `Ctrl-b $` | Rename current session |
| `Ctrl-b s` | List/switch sessions (interactive) |
| `Ctrl-b (` | Previous session |
| `Ctrl-b )` | Next session |
| `Ctrl-b L` | Last (most recent) session |

---

## Windows

| Key | Action |
|-----|--------|
| `Ctrl-b c` | Create new window |
| `Ctrl-b ,` | Rename current window |
| `Ctrl-b &` | Kill current window |
| `Ctrl-b w` | List/switch windows (interactive) |
| `Ctrl-b p` | Previous window |
| `Ctrl-b n` | Next window |
| `Ctrl-b 0-9` | Switch to window by index |
| `Ctrl-b '` | Switch to window by index (prompt) |
| `Ctrl-b .` | Move window to a new index |
| `Ctrl-b f` | Find window by name |

### Reorder windows

```bash
# Inside tmux command mode (Ctrl-b :)
swap-window -t -1       # move current window left
swap-window -t +1       # move current window right
swap-window -s 2 -t 0   # swap window 2 and window 0
move-window -t 0        # move current window to index 0
```

---

## Panes

| Key | Action |
|-----|--------|
| `Ctrl-b %` | Split vertically (side by side) |
| `Ctrl-b "` | Split horizontally (top/bottom) |
| `Ctrl-b o` | Cycle to next pane |
| `Ctrl-b ;` | Toggle between last two panes |
| `Ctrl-b x` | Kill current pane |
| `Ctrl-b z` | Zoom/unzoom pane (toggle fullscreen) |
| `Ctrl-b q` | Show pane numbers (press number to jump) |
| `Ctrl-b {` | Swap pane with previous |
| `Ctrl-b }` | Swap pane with next |
| `Ctrl-b !` | Break pane into its own window |
| `Ctrl-b Space` | Cycle through layouts |
| `Ctrl-b ↑↓←→` | Move focus to pane in direction |
| `Ctrl-b Ctrl-↑↓←→` | Resize pane (repeat to continue) |
| `Ctrl-b Alt-↑↓←→` | Resize pane in larger steps |

### Pane layouts

```
even-horizontal   even-vertical   main-horizontal   main-vertical   tiled
```

Switch with `Ctrl-b Space` or set explicitly:
```bash
select-layout main-vertical
select-layout tiled
```

### Join/break panes

```bash
# In command mode (Ctrl-b :)
join-pane -s :1         # pull window 1 into current window as a pane
join-pane -t :2         # send current pane to window 2
break-pane              # break current pane into its own window
swap-pane -U            # swap with pane above
swap-pane -t 1          # swap current pane with pane 1
```

### Resize pane precisely

```bash
resize-pane -D 5        # down 5 lines
resize-pane -U 5        # up 5 lines
resize-pane -L 10       # left 10 cols
resize-pane -R 10       # right 10 cols
resize-pane -x 80       # set width to 80
resize-pane -y 24       # set height to 24
```

---

## Copy Mode (Scrollback)

Enter copy mode with `Ctrl-b [`. Uses vi or emacs keys depending on config.

### vi keys (recommended)

| Key | Action |
|-----|--------|
| `Ctrl-b [` | Enter copy mode |
| `q` | Exit copy mode |
| `↑ / k` | Scroll up |
| `↓ / j` | Scroll down |
| `Ctrl-u` | Scroll up half page |
| `Ctrl-d` | Scroll down half page |
| `g` | Go to top |
| `G` | Go to bottom |
| `/` | Search forward |
| `?` | Search backward |
| `n` | Next search match |
| `N` | Previous search match |
| `Space` | Start selection |
| `Enter` | Copy selection, exit copy mode |
| `Ctrl-b ]` | Paste copied text |

Enable vi keys in `~/.tmux.conf`:
```bash
set -g mode-keys vi
```

### Mouse scroll

```bash
set -g mouse on         # enables scroll with mouse wheel
```

---

## Configuration: ~/.tmux.conf

### Essentials

```bash
# Change prefix to Ctrl-a (screen-style)
unbind C-b
set -g prefix C-a
bind C-a send-prefix

# Reload config
bind r source-file ~/.tmux.conf \; display "Config reloaded"

# Start window/pane index at 1
set -g base-index 1
setw -g pane-base-index 1

# Re-number windows after closing
set -g renumber-windows on

# Keep window name fixed
set -g allow-rename off

# Increase scrollback buffer
set -g history-limit 50000

# Mouse support
set -g mouse on

# Vi copy mode
set -g mode-keys vi

# Faster key response
set -sg escape-time 10
set -g repeat-time 600

# Focus events (for vim/nvim)
set -g focus-events on

# True color support
set -g default-terminal "tmux-256color"
set -ag terminal-overrides ",xterm-256color:RGB"
```

### Intuitive splits (open in current path)

```bash
bind | split-window -h -c "#{pane_current_path}"
bind - split-window -v -c "#{pane_current_path}"
unbind %
unbind '"'
```

### Vim-style pane navigation

```bash
bind h select-pane -L
bind j select-pane -D
bind k select-pane -U
bind l select-pane -R
```

### Resize panes with vim keys

```bash
bind -r H resize-pane -L 5
bind -r J resize-pane -D 5
bind -r K resize-pane -U 5
bind -r L resize-pane -R 5
```

### Better copy mode

```bash
bind -T copy-mode-vi v send -X begin-selection
bind -T copy-mode-vi y send -X copy-pipe-and-cancel "pbcopy"   # macOS
# bind -T copy-mode-vi y send -X copy-pipe-and-cancel "xclip -sel clip"  # Linux
bind -T copy-mode-vi r send -X rectangle-toggle
```

### Status bar

```bash
set -g status-interval 5
set -g status-left-length 40
set -g status-left "#[fg=green]#S #[fg=yellow]#I:#P"
set -g status-right "#[fg=cyan]%d %b %R"
set -g status-justify centre
setw -g window-status-current-style fg=white,bold,bg=red
```

### Reload config

```bash
# From CLI
tmux source ~/.tmux.conf

# From inside tmux (Ctrl-b :)
source-file ~/.tmux.conf
```

---

## Plugin Manager (TPM)

### Install TPM

```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

Add to `~/.tmux.conf`:

```bash
# Plugins
set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'tmux-plugins/tmux-resurrect'
set -g @plugin 'tmux-plugins/tmux-continuum'
set -g @plugin 'tmux-plugins/tmux-yank'

# Initialize TPM (keep at bottom)
run '~/.tmux/plugins/tpm/tpm'
```

| Key | Action |
|-----|--------|
| `Ctrl-b I` | Install plugins |
| `Ctrl-b U` | Update plugins |
| `Ctrl-b Alt-u` | Remove unused plugins |

### Useful plugins

| Plugin | Purpose |
|--------|---------|
| `tmux-sensible` | Sane defaults everyone agrees on |
| `tmux-resurrect` | Save/restore sessions across reboots |
| `tmux-continuum` | Auto-save sessions every 15 min |
| `tmux-yank` | Copy to system clipboard in copy mode |
| `tmux-fzf` | Fuzzy-find sessions/windows/panes |
| `catppuccin/tmux` | Popular theme |
| `tmux-cpu` | CPU/memory in status bar |

---

## Scripting & Automation

### Create a pre-configured session

```bash
#!/bin/bash
SESSION="dev"

tmux new-session -d -s $SESSION -n editor
tmux send-keys -t $SESSION:editor "nvim ." Enter

tmux new-window -t $SESSION -n server
tmux send-keys -t $SESSION:server "npm run dev" Enter

tmux new-window -t $SESSION -n git
tmux split-window -h -t $SESSION:git
tmux send-keys -t $SESSION:git "git log --oneline" Enter

tmux select-window -t $SESSION:editor
tmux attach -t $SESSION
```

### Key scripting commands

```bash
tmux new-session -d -s name           # create detached session
tmux new-window -t session:           # add window
tmux split-window -h/-v -t target     # split pane
tmux send-keys -t target "cmd" Enter  # send command to pane
tmux select-window -t session:name    # focus window
tmux select-pane -t session:win.pane  # focus pane
tmux has-session -t name              # check if session exists (exit code)
```

### Target syntax

```
session:window.pane
work:editor.1       # session "work", window "editor", pane 1
:2.0                # current session, window 2, pane 0
```

### Run command in all panes

```bash
# Enable pane synchronization (Ctrl-b :)
setw synchronize-panes on
# All keystrokes go to every pane in the window
setw synchronize-panes off
```

---

## Shared Sessions (Pair Programming)

```bash
# Both users connect to same socket
tmux -S /tmp/shared new -s pair
chmod 777 /tmp/shared

# Second user joins
tmux -S /tmp/shared attach -t pair

# Read-only observer
tmux -S /tmp/shared attach -t pair -r
```

---

## Resurrect & Persistence

With `tmux-resurrect`:

| Key | Action |
|-----|--------|
| `Ctrl-b Ctrl-s` | Save session |
| `Ctrl-b Ctrl-r` | Restore session |

With `tmux-continuum`, add to config:
```bash
set -g @continuum-restore 'on'    # auto-restore on tmux start
set -g @continuum-save-interval '15'
```

---

## Troubleshooting

### Colors look wrong
```bash
# Add to ~/.tmux.conf
set -g default-terminal "tmux-256color"
set -ag terminal-overrides ",xterm-256color:RGB"

# Add to ~/.zshrc or ~/.bashrc
export TERM=xterm-256color
```

### Escape key delay in vim/nvim
```bash
set -sg escape-time 10
```

### Clipboard not working on macOS
```bash
# Install reattach-to-user-namespace
brew install reattach-to-user-namespace
set -g default-command "reattach-to-user-namespace -l zsh"
# Or use tmux-yank plugin (preferred)
```

### SSH session drops
```bash
# Keep SSH alive through tmux
set -g @continuum-restore 'on'
# In ~/.ssh/config:
# ServerAliveInterval 60
# ServerAliveCountMax 3
```

### tmux nested (local + remote)
```bash
# Press Ctrl-b twice to send prefix to inner session
# Or bind a different prefix for local vs remote
```

---

## Quick Reference

```
Sessions          Windows           Panes
─────────         ───────           ─────
new  -s name      c  new            %  vsplit
ls                ,  rename         "  hsplit
a   -t name       &  kill           x  kill
kill-session      w  list           o  next
kill-server       p/n prev/next     z  zoom
                  0-9 jump          q  show #
d   detach        .  move index     !  break out
$   rename        f  find           {/}  swap
s   list+switch                     Space layouts
(/)) prev/next                      ↑↓←→ navigate
```

---

## FAQ

### How do I keep window names fixed?

```bash
set -g allow-rename off
```

### Where is .tmux.conf?

`~/.tmux.conf` — create it if it doesn't exist.

### How do I reload config without restarting?

```bash
tmux source ~/.tmux.conf
# or inside tmux: Ctrl-b :source-file ~/.tmux.conf
```

### How do I scroll up?

`Ctrl-b [` to enter copy mode, then arrow keys or `Ctrl-u/d`. `q` to exit.

### How do I copy text?

1. `Ctrl-b [` — enter copy mode
2. `Space` — start selection (vi mode) or `Ctrl-Space` (emacs)
3. Move cursor to end of selection
4. `Enter` — copy
5. `Ctrl-b ]` — paste

### How do I list all keybindings?

```bash
tmux list-keys | less
# or inside tmux: Ctrl-b ?
```

### How do I move a pane to another window?

```bash
# Ctrl-b : then:
join-pane -t :2         # move current pane to window 2
break-pane              # break pane into its own window
```

### How do I run the same command in all panes?

```bash
# Ctrl-b : then:
setw synchronize-panes on
# type command — it goes to all panes
setw synchronize-panes off
```

### How do I make tmux start automatically?

Add to `~/.zshrc` or `~/.bashrc`:
```bash
if [ -z "$TMUX" ]; then
  tmux attach -t default || tmux new -s default
fi
```
