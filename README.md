# Project Board

A kanban board per project — drag cards across columns, tag them, and the board travels with the repo.

A [workspacer](https://github.com/DJTouchette/workspacer) hub plugin (webview). It opens as an agent-scoped pane and keeps one board per project directory.

## What it does

The board lives at `.workspacer/plugins/project-board/board.json` inside the project (workspacer ≥ 0.137), written through cwd-scoped `fs.write` — commit it to share the board, gitignore it to keep it local.

- **Columns** — starts with Backlog / In Progress / Done; add, rename, and remove your own.
- **Cards** — title + optional notes, created inline, dragged between and within columns with live drop indicators.
- **Tags** — comma-separated per card; each tag keeps a stable color from a colorblind-safe palette, and clicking a tag filters the board.
- **Autosave** — debounced writes, flush on blur; last-write-wins per file.

## Install

Command palette → **Install Plugin…** → `DJTouchette/workspacer-plugin-project-board`

## Permissions

| Capability | Scope | Why |
|---|---|---|
| `fs.read` | agent cwd | read `board.json` |
| `fs.write` | agent cwd | save it |

No events consumed, no network, no sidecar process.
