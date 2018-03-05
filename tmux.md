# Tmux configuration that compliments defaults

Ever felt the need to extend default tmux configuration without actually hamperning any of the defaults? Then use the following options.

- Windows navigation using `Alt-number`
- Jump between recent windows using `Alt-tab`
- Switch between panes using `Alt-arrow` keys
- Mouse mode on for those who like to click around
- Easier splitting with more intuitive `|` and `-` keys
- Vi key-bindings in copy mode
- Prettier but still simple statsline

Paste following configuration into your `~/.tmux.conf`

```
# Set vi key-bindings for selection mode
set-window-option -g mode-keys vi
bind-key -t vi-copy 'v' begin-selection
bind-key -t vi-copy 'y' copy-selection

# switch windows with Alt+number
# Make sure that Alt key is set to be the Meta key in your terminal emulator
bind-key -n M-0 select-window -t 0
bind-key -n M-1 select-window -t 1
bind-key -n M-2 select-window -t 2
bind-key -n M-3 select-window -t 3
bind-key -n M-4 select-window -t 4
bind-key -n M-5 select-window -t 5
bind-key -n M-6 select-window -t 6
bind-key -n M-7 select-window -t 7
bind-key -n M-8 select-window -t 8
bind-key -n M-9 select-window -t 9

# Alt+Tab to switch to last active window
bind-key -n M-tab last-window

# fast pane switching
# Use Alt+arrow keys without prefix key to switch panes
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# Ctrl and hjkl to switch between panes
# Ctrl-\ to switch to last active pane
bind-key -n C-h select-pane -L
bind-key -n C-j select-pane -D
bind-key -n C-k select-pane -U
bind-key -n C-l select-pane -R
bind-key -n C-\ select-pane -l

# Alternate prefix Ctrl+Space
set -g prefix2 C-Space

# use Prefix+| to split window horizontally and Prefix+- to split vertically
bind | split-window -h -c "#{pane_current_path}"
bind - split-window -v -c "#{pane_current_path}"

# Reload tmux configuration
bind r source-file ~/.tmux.conf \; display-message "Config reloaded..."

# status line
set-option -g status-left-length "80"

set-window-option -g status-bg colour234

set-window-option -g status-left " [#S] "
set-window-option -g status-left-fg black
set-window-option -g status-left-bg white

set-window-option -g status-right " [#H] [%H:%M %d-%b-%y] "
set-window-option -g status-right-fg black
set-window-option -g status-right-bg white

set-window-option -g window-status-format " #I: #W "
set-window-option -g window-status-fg white
set-window-option -g window-status-bg colour238

set-window-option -g window-status-current-format " #I: #W "
set-window-option -g window-status-current-fg colour233
set-window-option -g window-status-current-bg cyan
set-window-option -g window-status-current-style regular


# Start windows at 1
set -g base-index 1

# Enable mouse mode by default for tmux version >= 2.1
setw -g mode-mouse on

# Enable mouse mode by default for tmux version < 2.1
# set -g mode-mouse on
# set -g mouse-resize-pane on
# set -g mouse-select-pane on
# set -g mouse-select-window on

# Allow mouse to select which pane to use
set -g mouse-select-pane on

# Allow mouse dragging to resize panes
set -g mouse-resize-pane on

# Allow mouse to select windows
set -g mouse-select-window on
```
