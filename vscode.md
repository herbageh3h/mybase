# Quick Start

- code .
- vscodevim, vspacecode

```
Cmd+Shift+p    "Command palette.
Cmd+w          "Close window.
Cmd+b          "Toggle sidebar.
Ctrl+`         "Terminal.
Cmd+Shift+e    "Explorer.
Ctrl+tab       "Switch editor tab.
Ctrl + n => new file
Ctrl + 1 => switch to editor
Command + p => quick open
Ctrl + r => reopen
Command + Shift + f => search
Ctrl + Shift + g => source control
Command + Shift + d => debug
Command + Shift + x => extension
```


# Shortcuts

```
Command + p => quick open
Command + b => toggle sidebar
Ctrl + ` => toggle termial
Command + 1/2/3... => switch editor
Command + Shift + p => open command palette
Ctrl + g => goto line number
Ctrl + Shift + Tab => show the active file
Command + Shift + t => reopen closed editor
Command + , => preference
Command + +/- => zoom
Command + w => close window
Command + Shift + e => explorer
Command + Shift + f => search
Command + Shift + d => debug
Ctrl + . => suggest
Option + Shift + f => format
Ctrl + k, z => toggle zen mode
Command + f => search and replace
Ctrl + tab => switch editor
Command + , => settings
Ctrl + r => reopen
Command + Shift + m => problems
Cmd+<up>/Cmd+<down>    "Open/Close folder in explorer tree.
```


# Roadmap

- shortcuts


# Tutorial

- command palette
- toggle sidebar
- toggle terminal
- open user setting
- open file
- navigate through tab
- split window
- close file
- full text search
- comment
- multi cursor
- expand selection
- rename symbol
- go to definition
- move line up


# Tips

1. Toggle mini maps off.
2. Try zen mode.
3. Turn word wrap on.


# Settings

- editor.minimap.enabled = false
- files.autoGuessEncoding = true
- workbench.editor.enablePreview = false


# Links

1. Visual Studio Crash Course. by freeCodeCamp.org, youtube
2. [Improved Vim setup in Visual Studio Code](https://hoitz.medium.com/improved-vim-setup-in-visual-studio-code-bc579501b80c)


# FAQ

## How to solve file encoding problem?

```
Command + , | files.autoGuessEncoding = true
```

## How to download offline plugins?

Go to <https://marketplace.visualstudio.com> download .vsix plugins.

In vscode, extensions -> install from vsix.

## How to open settings.json?

Open command palette, type "open settings", edit json file.

## How to use .vimrc?

Open settings -> Type vimrc -> Enable "Use Keymapping from a .vimrc file" option

.vimrc ususally found in ~/.vimrc.

## How to use copy and paste?

Open settings json, add following config.

```
"vim.useSystemClipboard": true
```

## How to use command palette?

Use cmd+shift+p to open dialogue.

- >xx :: search action
- xx :: search file
- @xx :: search current structure
- #xx :: search global symbol

## How to write markdown files?

Use extension `Markdown All in One`.

- cmd+' v :: Open preview to the side.
