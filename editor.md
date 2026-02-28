# Editor

## Keys

- Special key :: <ctrl>, <cmd>, <alt>, <shift>, <space>, <left>, <right>, <up>, <down>
- Leader key :: <space> or , or \

## Actions

IDE Commands.

- Command palette      :: cmd+shift+p                      # Show All Commands
- Settings             :: cmd+,                            # Preferences: Open User Settings
- Toggle zen mode      :: cmd+z                            # View: Toggle Zen Mode
- Toggle full screen mode :: cmd+shift+z                   # View: Toggle Full Screen
- Select next in quick open  :: ctrl+n                     # Select Next in Quick Open, selectNextSuggestion
- Select previous in quick open  :: ctrl+p                 # Select Previous in Quick Open, selectPrevSuggestion
- IDE lead key         :: cmd+'                            # Leader Key

Frequent commands.

- Open files           :: cmd+e                            # Go to File
- Open recent files    :: cmd+r                            # File: Open Recent
- Full text search     :: cmd+shift+f                      # Search: Find in Files
- Comment              :: cmd+/                            # Toggle Line Comment
- Comment block        :: cmd+shift+/                      # Toggle Block Comment
- View: zoom out       :: cmd+=                            # View: Zoom In                                   # Increase Font Size
- View: zoom in        :: cmd+-                            # View: Zoom Out                                  # Decrease Font Size
- Expand selection     :: cmd+shift+right                  # Expand Selection
- Shrink selection     :: cmd+shift+left                   # Shrink Selection
- Expand line selection      :: ctrl+cmd+l                 # Expand Line Selection
- New file in explorer :: ctrl+cmd+n                       # File: New File
- New folder in explorer :: ctrl+cmd+shift+n               # File: New Folder

Window commands.

- Toggle side bar      :: cmd+1                            # View: Toggle Side Bar Visibility
- Toggle bottom panel  :: cmd+2                            # View: Toggle Panel
- Go to explorer       :: cmd+shift+1                      # View: Show Explorer
- Go to terminal       :: cmd+shift+2                      # View: Toggle Terminal
- Toggle console       :: cmd+4                            # View: Toggle Output
- View: show extensions      :: cmd+6                      # View: Show Extensions
- Split editor right   :: cmd+]                            # View: Split Editor
- Split editor down    :: cmd+[                            # View: Split Editor Down
- Navigate split window :: cmd+h                           # View: Focus Left Editor Group
- Navigate split window :: cmd+j                           # View: Focus Editor Group Below
- Navigate split window :: md+k                            # View: Focus Editor Group Above
- Navigate split window :: cmd+l                           # View: Focus Right Editor Group
- Max panel            :: cmd+ctrl+2                       # View: Toggle Maximized Panel

Tab commands.

- Close editor tab     :: cmd+w                            # View: Close Editor
- View: reopen closed tab    :: cmd+shift+r                # View: Reopen Closed Editor
- Open previous tab    :: cmd+h                            # View: Open Previous Editor
- Open next tab        :: cmd+l                            # View: Open Next Editor

Explorer commands.
- Collapse folders     :: cmd+ctrl+c                       # Collapse Folders in Explorer
- Reveal in explorer   :: cmd+ctrl+f                       # File: Reveal Active File in Explorer View

Edit commands.

- Move one line up     :: cmd+shift+k                      # Move Line Up
- Move one line down   :: cmd+shift+j                      # Move Line Down

Multi cursors.

- Add cursor below                      :: cmd+alt+<down>
- Add cursor above                      :: cmd+alt+<up>
- Add selection to next find match      :: cmd+d
- Move Last Selection To Next Find Match         :: cmd+shift+d      # Move Last Selection To Next Find Match
- Add all selection match               :: cmd+shift+d
- Cursor undo                           :: cmd+u
- Cursor redo
- Add selection to previous find match
- Select all occurrences of find match

Settings

- Preferences: open keyboard shortcuts :: cmd+' cmd+s

Coding commands.

- Code completion      :: cmd+.                            # Trigger Suggest                                 # Code Completion > SmartType
- Show parameter hint  :: cmd+p                            # Trigger Parameter Hints                         # View > Parameter Info
- Hide parameter hint  :: cmd+ctrl+p                       # closeParameterHints
- Format code          :: cmd+shift+l                      # Format Document                                 # Code > Reformat Code
- Quick fix            :: cmd+enter                        # Quick Fix
- Rename               :: ctrl+cmd+r                       # renameFile                                      # Refactor > Rename
- Go to symbol         :: cmd+shift+;                      # Go to symbol in Editor
- Rename symbol        :: ctrl+cmd+r
- Go to definition     :: cmd+b
- Go to test           :: cmd+shift+t
- Generate test data   :: cmd+t

## editorconfig

```text
```

## Task

### 1. Open fils
### 2. Install plugins
### 3. Switch windows

## FAQ

### How to use multi cursor on vscode?

1. use visual mode to select a word
2. use cmd+d to select current word into cursor
3. use cmd+d to select next matching word into cursor
4. use cmd+shift+d to skip next matching word
