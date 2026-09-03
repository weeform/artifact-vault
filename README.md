# Artifact Vault

Browse AI-generated files like an Obsidian vault — HTML, Markdown, JSON, TXT, images, PDF, audio & video, rendered right in your browser. Zero install, read-only, nothing leaves your machine.

<!-- TODO: screenshot (docs/screenshot.png) — file tree + rendered HTML preview -->

## Why

AI tools constantly produce rich files — HTML reports, Markdown notes, JSON dumps, diagrams, images. Obsidian is great for editing Markdown, but it won't render your HTML, and it wants to own your folder as a vault.

Artifact Vault takes the opposite trade: **no editing, maximum viewing compatibility.** Drop one `index.html` into any folder, open it in your browser, and everything the AI produced is one click away.

## Quick Start

1. Download [`index.html`](./index.html)
2. Copy it into the root of any folder you want to browse
3. Double-click to open it in Chrome or Edge
4. Click **"📁 Choose Root Folder to Start"** and grant read access — done

Each copy of `index.html` remembers its own authorized folder independently (stored in your browser's IndexedDB), so authorization is a one-time step per folder.

## Supported Formats

| Category | Formats | Rendering |
|----------|---------|-----------|
| Markdown | `md` `markdown` `mdown` `mkd` | Fully rendered (marked + highlight.js, built-in fallback renderer offline) |
| HTML | `html` `htm` `xhtml` | Fully rendered, local CSS inlined, relative images resolved |
| Images | `png` `jpg` `gif` `webp` `svg` `avif` `bmp` `ico` | Native browser decoding |
| Documents | `pdf` | Native PDF viewer |
| Video | `mp4` `webm` `ogv` `mov` `m4v` | Native playback |
| Audio | `mp3` `wav` `ogg` `flac` `m4a` `aac` `opus` | Native playback |
| Code / Text | `json` `txt` `log` `csv` `yaml` `xml` `py` `js` `ts` `sh` … | Syntax highlighted, GBK/charset auto-detection |
| Other | unknown extensions | Sniffed: shown as text, or marked as binary |

Anything Obsidian leaves as raw text or refuses to open renders here.

## Features

- **VS Code-style file tree** — lazy loading, drag-to-resize, directory state preserved on refresh
- **Zero install** — no server, no build, no dependencies to install; works on locked-down machines where you can't install software
- **New-tab view** — open any file in a clean standalone tab (no UI chrome), ideal for full-page screenshots; relative images are inlined so the document is fully self-contained
- **Locate on disk** — jump to the file's containing folder
- **Safe by design** — previews run in sandboxed iframes with scripts disabled; read-only access only

## Privacy & Security

- **Read-only** — uses the File System Access API in `read` mode; the page cannot write, move, or delete anything
- **Local only** — no telemetry, no accounts, no upload path. Your files never leave the machine
- **Sandboxed previews** — HTML/Markdown render inside sandboxed iframes; embedded scripts do not execute
- **Permission memory** — folder grants are stored locally in IndexedDB, one record per deployed copy

## Browser Support

| Browser | Status |
|---------|--------|
| Chrome / Edge (Chromium) | ✅ Fully supported |
| Firefox | 🚧 Planned (fallback via `webkitdirectory`) |
| Safari | 🚧 Planned (fallback via `webkitdirectory`) |

The directory-access API used today (`showDirectoryPicker`) is Chromium-only. A universal fallback is on the roadmap — see below.

## Roadmap

- [ ] Vendor marked & highlight.js into the file — fully offline, zero CDN
- [ ] Firefox / Safari support via `webkitdirectory` fallback
- [ ] Obsidian vault syntax: `[[wikilinks]]`, `![[embeds]]`, callouts
- [ ] Office formats: docx / xlsx / pptx, EPUB
- [ ] Full-text search across the folder

## FAQ

**Why not just open the folder in Obsidian?**
Obsidian renders only Markdown; HTML shows as raw code or a broken embed, and JSON/images/code get no special treatment. It also asks to convert your folder into a vault. Artifact Vault is read-only and renders everything the browser can.

**Why copy `index.html` into each folder?**
No server means no install — but browser security requires the page itself to request folder access, and each deployment location keeps its own permission memory. In practice: one click, once per folder.

**Can it edit files?**
No, by design. Read-only is the safety guarantee that lets you point it at folders shared with other tools (Obsidian, editors, sync clients) without risk.

## License

Released under the [MIT License](./LICENSE).
