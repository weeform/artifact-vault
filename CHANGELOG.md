# Changelog

Notable changes to Artifact Vault are documented here. Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).

## Unreleased

### Added

- Mermaid diagram rendering — ` ```mermaid ` fences in Markdown render as diagrams (dark theme) in both the preview and the new-tab view; malformed diagrams fall back to the source with an error note. Diagrams are rendered to static SVG in the page before entering the sandboxed iframe, so no scripts are added to previews. Mermaid v11.17.2 vendored inline — `index.html` grows to ~3.7 MB.

## 0.1.0 — 2026-09-03

Initial public release.

### Added

- Version badge in the top bar (`v0.1.0`) — cite it in bug reports
- VS Code-style file tree — lazy loading, drag-to-resize, directory state preserved on refresh
- Rendered previews — Markdown, HTML (local CSS inlined, relative images resolved), images, PDF, audio, video
- Syntax-highlighted code/text with charset auto-detection (BOM / declared encoding / GBK heuristic)
- New-tab view — any file in a clean standalone tab, relative images inlined so the document is self-contained
- Locate on disk — jump to the file's containing folder
- Read-only folder access via the File System Access API; per-folder permission memory in IndexedDB
- marked v12.0.2 and highlight.js v11.9.0 vendored inline — zero CDN, fully offline
