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
# switch windows with Alt+number. e.g Alt+5 selects window #5.
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

# Alternate prefix Ctrl+Space instead of the default Ctrl+b
set -g prefix2 C-Space

# use Prefix+| to split window horizontally and Prefix+- to split vertically
bind | split-window -h -c "#{pane_current_path}"
bind - split-window -v -c "#{pane_current_path}"

# fast pane switching
# Use Alt+arrow keys without prefix key to switch panes
bind-key -n M-Left select-pane -L
bind-key -n M-Right select-pane -R
bind-key -n M-Up select-pane -U
bind-key -n M-Down select-pane -D

# Reload tmux configuration
bind r source-file ~/.tmux.conf \; display-message "Config reloaded..."

# Start windows at 1
set -g base-index 1

# Enable mouse mode by default for tmux version >= 2.1
setw -g mouse on

# Set vi key-bindings for selection mode
set-window-option -g mode-keys vi
bind-key -T copy-mode-vi v send-keys -X begin-selection
bind-key -T copy-mode-vi y send-keys -X copy-selection

# status line
set-option -g status-left-length "80"

set-window-option -g status-style bg=colour234

set-window-option -g status-left " [#H] "
set-window-option -g status-left-style fg=black,bg=white

set-window-option -g status-right " [#(date \"+%Y-%b-%d %H:%M\")] "
set-window-option -g status-right-style fg=black,bg=white

set-window-option -g window-status-format " #I: #W "
set-window-option -g window-status-style fg=white,bg=colour238

set-window-option -g window-status-current-format " #I: #W "
set-window-option -g window-status-current-style fg=colour233,bg=cyan
```
