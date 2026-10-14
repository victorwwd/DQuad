<p align="right">
  <b>English</b> · <a href="README.zh-CN.md">简体中文</a>
</p>

<p align="center">
  <h1 align="center">DQuad</h1>
  <p align="center">Multi-pane file manager for Windows</p>
  <p align="center">
    <a href="#features">Features</a> •
    <a href="#usage">Usage</a> •
    <a href="#configuration">Configuration</a> •
    <a href="#license">License</a>
  </p>
</p>

---

A lightweight Windows file manager with flexible multi-pane layouts, tabs, bookmark management, file tags, Everything-powered whole-disk search, and UNC network path access.

<img width="1920" height="1040" alt="image" src="https://github.com/user-attachments/assets/3aeee169-961e-42d3-9a60-baa46f8e0b00" />

## Features

- **Flexible layouts** — 8 layout modes: single pane / two panes (horizontal or vertical) / three panes (4 variants) / four panes 2×2 (default), switchable from the View menu
- **Tabs** — An independent tab bar per pane, with new/close/switch, drag-to-reorder, duplicate tab, close others, and history navigation
- **Bookmarks** — Grouping, drag-to-reorder, import/export
- **File tags** — NTFS ADS–based file tagging with colors and groups, a tag manager, filter by tag, and find files by tag
- **Everything search** — Integrated Everything whole-disk search engine (`Ctrl+F`, or the search button at the right of the address bar: left-click searches the current folder, right-click searches all drives). Supports regex, case-sensitive, and whole-word matching. Results have four columns (Name / Folder / Type / Size): click a column header to sort, double-click to open, or right-click to open the containing folder (reveals and selects it), copy the path, or copy the file name
- **Image preview** — Asynchronous image thumbnail loading in large-icon view, with viewport-aware progressive loading
- **Breadcrumb navigation** — Segmented path display; click any parent folder to jump to it, right-click to edit, copy, or paste a path
- **File operations** — Copy, cut, paste, delete, and rename, plus cross-pane file drag & drop, with no limit on the number of files
- **View modes** — Details and large icons
- **Left navigation** — "This PC" drive tree (with free-space bars and automatic refresh on USB hot-plug) and Recycle Bin (with restore)
- **New file** — Create txt/md/py/bat/ps1/c/h files and Office documents (docx/xlsx/pptx), integrating the Shell "New" menu
- **Custom commands** — A configurable quick-command menu with placeholder substitution and a graphical command editor (add/edit/delete/reorder/duplicate)
- **Shell integration** — Native context menus with timeout protection so third-party Shell extensions cannot hang the main window; copy path, send to desktop shortcut / USB drive
- **UNC network paths** — Access `\\server\share` paths, with asynchronous reachability checks
- **Encrypted file detection** — Asynchronously detects files encrypted by encryption software and marks them with a lock icon
- **Directory monitoring** — Automatic refresh on file changes (via `ReadDirectoryChangesW`)
- **Settings dialog** — Session restore, default paths, context-menu preloading, smart paste, shell integration, automatic updates, and more
- **State persistence** — Window layout, tab state, and view settings are saved automatically
- **Crash protection** — VEH/UEH exception handling plus watchdog hang detection, with automatic minidump generation
- **Automatic updates** — Check for and download new releases from GitHub
- **Light/dark theme** — The window title bar follows the system light/dark theme
- **Single instance** — Prevents duplicate launches

## Usage

Download the latest `DQuad.exe` from [Releases](https://github.com/victorwwd/DQuad/releases), then run it directly — no installation required.

### Keyboard shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+T` | New tab |
| `Ctrl+Shift+T` | Set a tag on the selected file |
| `Ctrl+W` | Close tab |
| `Ctrl+D` | Add the current path to bookmarks |
| `Ctrl+B` | Show/hide the bookmarks panel |
| `Ctrl+F` | Open Everything search |
| `Ctrl+C/X/V` | Copy / cut / paste |
| `Ctrl+Shift+C` | Copy the full path of the selection (copies the current folder when nothing is selected) |
| `Ctrl+A` | Select all |
| `Space` | QuickLook preview of the selected item |
| `F2` | Rename |
| `F5` | Refresh |
| `Del` | Delete to Recycle Bin |
| `Shift+Del` | Delete permanently |
| `Enter` | Open the selected file/folder |
| `ESC` | Close the search dialog |
| `Alt+F4` | Exit |

### Mouse actions

| Action | Area | Description |
|--------|------|-------------|
| Double-click a tab | Tab bar | Close that tab |
| Click empty space | Tab bar | New tab |
| Right-click a tab | Tab bar | Close / close others / duplicate tab |
| Drag a tab | Tab bar | Reorder, including across panes |
| Double-click a file | File list | Open with the system default program |
| Double-click a folder | File list | Enter that folder |
| Double-click empty space | File list | Go to the parent folder |
| Right-click empty space | File list | New / paste / refresh / filter by tag |
| Right-click a file | File list | Copy / cut / delete / rename / copy path / toggle tags / properties |
| Click a column header | File list | Sort by that column |
| Drag a file | Across panes | Cross-pane file drag & drop |
| Drag a bookmark | Bookmark tree | Move a bookmark into a group |
| Right-click a breadcrumb | Breadcrumb bar | Edit path / copy full path / paste path |
| Right-click the new-folder button | Toolbar | Single-click copies the current folder; double-click copies the selected item's path |
| Right-click the add-bookmark button | Toolbar | Choose a group to add to / create a group |

## Configuration

Configuration files live in the program directory and use UTF-8 encoded INI format:

| File | Description |
|------|-------------|
| `state.ini` | Window position, layout mode, pane paths, tab state, update settings, preload toggles, tip read state |
| `bookmarks.ini` | Bookmark tree structure (groups + items) |
| `commands.ini` | Custom commands for the toolbar menu |
| `tags.ini` | Tag definitions (name/color/group) and the file-tag index |

### Settings dialog

Open the settings dialog from the menu `Tools → Options` to configure:

| Category | Options |
|----------|---------|
| General | Restore the previous session on startup, default path for new tabs (Desktop / This PC / custom), context-menu preload toggle, smart paste (save clipboard image/text as a file when pasting), command configuration file management |
| Updates | Automatic update check toggle, check interval (days), check for updates now |
| Integration | Take over the system's folder-open handler, add "Open in DQuad" to the folder context menu (writes to the current user's HKCU registry only; clearing the checkbox removes it) |

### Custom commands

Click the terminal button on the toolbar to open the command menu; commands run as configured in `commands.ini`.

Manage them at `Tools → Options → General → Edit Commands...` (a graphical editor supporting add/edit/delete/reorder/duplicate).

Supported placeholders:

| Placeholder | Description |
|-------------|-------------|
| `{cwd}` | Current tab directory |
| `{sel}` | Full path of the first selected item in the current list (empty when nothing is selected) |
| `{name}` | File name of `{sel}` (empty when nothing is selected) |

Example command configuration:

```ini
[Command0]
name=Open current folder in Code
program=code
args="{cwd}"
confirm=0
enabled=1
```

Security policy: `confirm=1` always requires confirmation before execution; even when confirmation is not forced, a command containing high-risk keywords (`del`, `rd`, `format`, etc.) still triggers a confirmation prompt.

## License

[MPL 2.0 License](LICENSE)
