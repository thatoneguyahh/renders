# renders

A terminal + widget system that runs entirely in the browser. Type commands to open floating, draggable widgets for media, drawing, data visualization, and more — all from a retro green-on-black terminal interface.

**Live:** [renders.strangled.net](https://renders.strangled.net)

---

## Features

- **Terminal emulator** with a Unix-like shell: command history, tab completion, pipes (`|`), I/O redirection (`>`, `>>`, `<`), background processes (`&`), aliases, and environment variables
- **Floating widgets** — draggable, resizable, minimizable, and fullscreen-able windows rendered over the terminal
- **Virtual filesystem** — in-memory FS with `/home`, `/tmp`, `/etc`, `/proc`, `/imports`, and more; supports `ls`, `cd`, `cat`, `mkdir`, `rm`, `mv`, `cp`, `touch`, `ln`, `stat`, and others
- **File import** — drag and drop or use the toolbar `[ open ]` button; files are auto-detected and opened in the right widget
- **Peer-to-peer** — connect two sessions directly via WebRTC (powered by PeerJS) for messaging and file sharing
- **Mobile support** — dedicated input bar, shortcut keys, and touch-friendly drag/resize

---

## Widget Commands

| Command | Description |
|---|---|
| `embed <url>` | Embed a URL in an iframe widget; falls back through CORS proxies automatically |
| `webview <url>` | Open a URL in a navigable webview widget with back/forward/address bar |
| `video <file\|url>` | Play a video file or stream |
| `audio <file\|url>` | Play audio with waveform visualizer |
| `image <file\|url>` | View an image with zoom controls |
| `img <file\|url>` | Alias for `image` |
| `pdf <file\|url>` | View a PDF with page navigation |
| `html <file\|url>` | Render an HTML file |
| `draw` | Open a freehand drawing canvas with brush/eraser/color/size controls |
| `webgl [scene]` | Render a WebGL scene (rotating cube, particles, etc.) |
| `plot <expr>` | Plot a mathematical expression (e.g. `plot sin(x)*cos(x)`) |
| `chart <type> <data>` | Render a bar/line/pie chart from inline data |
| `graph` | Alias for `chart` |
| `peer` | Open the peer connection panel |
| `stream <url>` | Open a media stream |
| `preview <file>` | Auto-detect and preview a file |

---

## Window Management

| Command | Description |
|---|---|
| `show` | List all open widgets |
| `focus <id>` | Focus a specific widget |
| `resize <id> <w> <h>` | Resize a widget |
| `tile` | Tile all widgets |
| `cascade` | Cascade all widgets |
| `renders` | Show system info |

Use the macOS-style traffic light buttons on each widget to close (red), minimize (yellow), or fullscreen (green). Drag the titlebar to move, drag the corner grip to resize.

**Keyboard shortcut:** `Ctrl+Space` toggles focus between the terminal and the last focused widget.

---

## Shell Commands

renders supports a broad set of Unix commands:

**Text & files:** `cat`, `grep`, `head`, `tail`, `wc`, `sort`, `uniq`, `cut`, `paste`, `tr`, `sed`, `awk`, `find`, `diff`, `comm`, `nl`, `od`, `hexdump`, `rev`, `tac`, `tee`, `xargs`

**Filesystem:** `ls`, `cd`, `pwd`, `mkdir`, `rm`, `mv`, `cp`, `touch`, `ln`, `readlink`, `stat`, `chmod`, `df`, `du`, `basename`, `dirname`

**Shell:** `echo`, `printf`, `export`, `set`, `unset`, `env`, `alias`, `unalias`, `source`, `history`, `exit`

**System info:** `date`, `cal`, `uptime`, `whoami`, `hostname`, `uname`, `id`, `ps`, `kill`

**Math:** `bc`, `expr`, `seq`, `factor`

**Misc:** `base64`, `md5sum`, `sha256sum`, `sleep`, `yes`, `true`, `false`, `test`, `timeout`, `truncate`

> Most "network" commands (`curl`, `wget`, `ping`, `ssh`, `nmap`) and "editor" commands (`vim`, `nano`, `emacs`) are simulated stubs for terminal atmosphere.

---

## Configuration

Settings are persisted in `localStorage` under `renders_config`. Defaults:

```json
{
  "theme": "green",
  "font_size": 14,
  "scrollback_lines": 10000,
  "animation_fps": 60,
  "mobile_layout": "stack"
}
```

---

## Tech Stack

- Vanilla HTML/CSS/JavaScript — single file, no build step
- [PDF.js](https://mozilla.github.io/pdf.js/) for PDF rendering
- [Chart.js](https://www.chartjs.org/) for charts and graphs
- [PeerJS](https://peerjs.com/) for WebRTC peer connections
- CORS proxy fallbacks via corsproxy.io, allorigins.win, codetabs.com

---

## License

[Unlicense](https://unlicense.org) — public domain, do whatever you want.