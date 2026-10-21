# mochalate - tmux

A tmux theme for the [mochalate](https://github.com/mochalate-theme/nvim) colorscheme family, a cozy
fusion of [gruvbox](https://github.com/morhetz/gruvbox)'s warm earthiness and
[catppuccin](https://github.com/catppuccin/nvim)'s soft pastels in mochalate tones.

Dark-only. Warm brown-black backgrounds, burnt coral reds, amber yellows, sage greens and
muted teals.

## Requirements

- tmux 3.2+

## Installation

### Manual

```sh
mkdir -p ~/.config/tmux/plugins/mochalate
git clone https://github.com/mochalate-theme/tmux.git ~/.config/tmux/plugins/mochalate/tmux
```

Then add to your `~/.tmux.conf`:

```tmux
# Source the theme
source-file ~/.config/tmux/plugins/mochalate/tmux/mochalate_options.conf
source-file ~/.config/tmux/plugins/mochalate/tmux/mochalate_main.conf
```

Reload tmux:

```sh
tmux source-file ~/.tmux.conf
```

### With TPM

```tmux
set -g @plugin 'mochalate-theme/tmux'
```

Press `prefix + I` to install.

## Options

Set these **before** sourcing the theme:

### General

| Option | Values | Default | Description |
|--------|--------|---------|-------------|
| `@mochalate-status-left` | comma-separated modules | `session,directory` | Left status modules |
| `@mochalate-status-right` | comma-separated modules | `application,cpu,ram,date_time` | Right status modules |
| `@mochalate-status-left-separator` | string | ` ` | Separator between left modules |
| `@mochalate-status-right-separator` | string | ` ` | Separator between right modules |
| `@mochalate-status-interval` | number | `5` | Status refresh interval (seconds) |
| `@mochalate-clock-mode-style` | `12`, `24` | `24` | Clock format |
| `@mochalate-date_time-format` | strftime format | `%Y-%m-%d %H:%M` | Date/time module format ([strftime(3)](https://developer.apple.com/library/documentation/Darwin/Reference/ManPages/man3/strftime.3.html)) |
| `@mochalate-pane-border-status` | `off`, `top`, `bottom` | `off` | Pane border status line |
| `@mochalate-window-format` | tmux format | `#I:#W` | Window title format (e.g. `#I:#W`, `#W`, `#I:#W#F`) |
| `@mochalate-window-current-format` | tmux format | `#I:#W` | Current window title format |
| `@mochalate-window-style` | style string | `""` | Regular window text style |
| `@mochalate-window-current-style` | style string | `bold` | Current window text style |

### Module Styles

Customize text style for each module (empty = default):

| Option | Values | Default | Description |
|--------|--------|---------|-------------|
| `@mochalate-session-style` | style string | `""` | Session text style |
| `@mochalate-directory-style` | style string | `""` | Directory text style |
| `@mochalate-date_time-style` | style string | `""` | Date/time text style |
| `@mochalate-application-style` | style string | `""` | Application text style |
| `@mochalate-cpu-style` | style string | `""` | CPU text style |
| `@mochalate-ram-style` | style string | `""` | RAM text style |

Style values: `bold`, `italic`, `dim`, `underscore`, `blink`, `reverse`, `strikethrough`. Combine with commas: `"bold,italic"`.

### Status Modules

Available modules for `@mochalate-status-left` and `@mochalate-status-right`:

| Module | Description | Requires |
|--------|-------------|----------|
| `session` | Session name | - |
| `directory` | Current window name | - |
| `date_time` | Date and time | - |
| `user` | Username (`whoami`) | - |
| `host` | Hostname | - |
| `application` | Current pane command | - |
| `cpu` | CPU percentage | [tmux-cpu](https://github.com/tmux-plugins/tmux-cpu) |
| `ram` | RAM percentage | [tmux-cpu](https://github.com/tmux-plugins/tmux-cpu) |

### Date/time Format

`@mochalate-date_time-format` takes any [strftime(3)](https://developer.apple.com/library/documentation/Darwin/Reference/ManPages/man3/strftime.3.html) specifier. The
theme expands it with tmux's `#{T:}` formatter, so each `%` token is replaced at
render time; everything else (spaces, `-`, `:`, `/`, …) is printed as-is.

| Specifier | Meaning | Example |
|-----------|---------|---------|
| `%Y` | 4-digit year | `2026` |
| `%m` | Month, zero-padded (01-12) | `10` |
| `%d` | Day, zero-padded (01-31) | `13` |
| `%H` | Hour, 24-h (00-23) | `13` |
| `%M` | Minute (00-59) | `24` |
| `%S` | Second (00-59) | `05` |
| `%I` | Hour, 12-h (01-12) | `01` |
| `%p` | AM/PM | `PM` |
| `%a` | Abbreviated weekday | `Tue` |
| `%A` | Full weekday | `Tuesday` |
| `%b` | Abbreviated month | `Oct` |
| `%B` | Full month | `October` |
| `%j` | Day of year (001-366) | `286` |
| `%T` | Shorthand for `%H:%M:%S` | `13:24:05` |
| `%F` | Shorthand for `%Y-%m-%d` | `2026-10-13` |

Ready-made formats:

| Value | Renders as |
|-------|------------|
| `%Y-%m-%d %H:%M` (default) | `2026-10-13 13:24` |
| `%H:%M` | `13:24` |
| `%I:%M %p` | `01:24 PM` |
| `%a %H:%M` | `Tue 13:24` |
| `%a %b %d, %Y` | `Tue Oct 13, 2026` |
| `%d/%m/%Y %H:%M` | `13/10/2026 13:24` |

```tmux
set -g @mochalate-date_time-format "%H:%M"
```

Notes: use `%%` for a literal percent sign, and avoid `#{` (it would be parsed
as a tmux format expansion).

### Example Configuration

```tmux
# Custom modules
set -g @mochalate-status-left "session,directory"
set -g @mochalate-status-right "application,date_time"

# Module styles
set -g @mochalate-session-style "bold"
set -g @mochalate-directory-style "bold,italic"

# Date/time format
set -g @mochalate-date_time-format "%H:%M"

# Source the theme
source-file ~/.config/tmux/plugins/mochalate/tmux/mochalate_options.conf
source-file ~/.config/tmux/plugins/mochalate/tmux/mochalate_main.conf
```

## Palette

| | Normal | | Bright |
| --- | --- | --- | --- |
| black | `#2c261e` | bright black | `#7a6850` |
| red | `#d06850` | bright red | `#d88078` |
| green | `#a8b878` | bright green | `#b0c888` |
| yellow | `#d8a050` | bright yellow | `#e8b870` |
| blue | `#88a0c0` | bright blue | `#a0b8d0` |
| magenta | `#e0a060` | bright magenta | `#c8a0d0` |
| cyan | `#78a890` | bright cyan | `#90c0a8` |
| white | `#e8d5c4` | bright white | `#f5ead8` |

Background `#1c1815`, foreground `#e8d5c4`, cursor `#e8d5c4`, selection `#5c4030` on
`#f5ead8`.

## Credits

- [morhetz/gruvbox](https://github.com/morhetz/gruvbox): the warm, earthy foundation.
- [catppuccin/nvim](https://github.com/catppuccin/nvim): the soft pastel accent palette.

## License

[MIT](../ghostty/LICENSE)
