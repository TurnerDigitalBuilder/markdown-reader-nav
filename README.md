# Markdown Reader

This is a **simple, low-maintenance** single-file Markdown reader:

- Open any `.md` file (drag/drop or “Open .md”)
- **Table of contents** from `##` / `###` headings
- **Task list checkboxes** persist per-document in `localStorage`
- **Search** highlights matches
- Light/dark theme
- Export/Import checkbox progress as JSON
- Print-friendly

## Files

```
.
├── index.html                 # the app (open in a browser)
└── markdown.md  # example markdown (optional)
```

## How it works

- Markdown rendering: **marked.js** (GFM enabled)
- HTML sanitization: **DOMPurify**
- Search highlighting: **mark.js**
- Checkbox persistence:
  - Each document is identified by a SHA-1 hash of the markdown content
  - Checkbox keys use `{#id}` if present in the checklist line, e.g.
    `- [ ] Pi boots cleanly {#hw.boot}`
  - Otherwise a slug of the item text is used

## Markdown tips

### Frontmatter (optional)

If your markdown starts with:

```yaml
---
title: Engineering Document
version: v0.2
owner: Ben Ferrer
status: Current working configuration
---
```

…the app will use those fields for the header.

### Task lists

Use standard GitHub-style task lists:

```markdown
- [ ] Unchecked item {#stable.id}
- [x] Checked item {#stable.done}
```

The `{#...}` is optional but recommended to keep IDs stable.

## Notes

- Since this is a local HTML file, your browser may block “fetching” local files automatically; the app uses the file picker/drag-drop to load markdown reliably.
- Everything is stored locally in your browser (no server).

## License

MIT
