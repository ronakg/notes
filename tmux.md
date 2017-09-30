# Tmux configuration that compliments defaults

Ever felt the need to extend default tmux configuration without actually hamperning any of the defaults? Then use the following options.

- Windows navigation using `Alt-number`
- Jump between recent windows using `Alt-tab`
- Switch between panes using `Alt-arrow` keys
- Mouse mode on for those who like to click around
- Easier splitting with more intuitive `|` and `-` keys
- Vi key-bindings in copy mode
- Prettier but still simple statsline

```
set-window-option -g mode-keys vi
bind-key -t vi-copy 'v' begin-selection
bind-key -t vi-copy 'y' copy-selection

# switch windows with alt+number
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

# alt-tab to switch to last active window
bind-key -n M-tab last-window

# fast pane switching
# Use Alt-arrow keys without prefix key to switch panes
bind -n M-Left select-pane -L
bind -n M-Right select-pane -R
bind -n M-Up select-pane -U
bind -n M-Down select-pane -D

# Alternate prefix
set -g prefix2 C-Space

# use PREFIX | to split window horizontally and PREFIX - to split vertically
bind | split-window -h -c "#{pane_current_path}"
bind - split-window -v -c "#{pane_current_path}"

# Reload tmux configuration
bind r source-file ~/.tmux.conf \; display-message "Config reloaded..."

# status line
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


# start windows at 1
set -g base-index 1

setw -g mode-mouse on

# Allow mouse to select which pane to use
set -g mouse-select-pane on

# Allow mouse dragging to resize panes
set -g mouse-resize-pane on

# Allow mouse to select windows
set -g mouse-select-window on
```
