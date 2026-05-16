---
tags: [meta]
description: "What's new in each version of WikiNest."
---

# Changelog

All notable changes to WikiNest are listed here in reverse chronological order.

---

## Unreleased

### Added

- **Folder display-name rename from sidebar UI** — hover any folder in the sidebar to reveal a pencil icon. Clicking it opens an inline input; on confirm, WikiNest writes the new name to `_meta.json` inside that folder and commits the change. No manual file editing required.
- **Custom home page** — if `docs/home.md` exists, it is loaded automatically on first visit instead of `docs/index.md`. Use it for a landing page with navigation links, announcements, or a project overview.

---

## v1.2.0 — 2026-05-16

### Added

- **Expanded toolbar** — the Markdown toolbar now has 16 buttons: Bold, Italic, Strikethrough, Heading, Link, Image, Blockquote, Code, Code block, Unordered list, Ordered list, Task list, Table, Horizontal rule, Wiki link, and Frontmatter helper.
- **Display preferences** — new panel accessible from the toolbar with two toggles:
  - *Show table of contents* — show or hide the "On this page" TOC in the sidebar
  - *Split preview* — switch between split-view (edit + preview) and edit-only mode
- **Print / PDF** — print icon added to the toolbar. Triggers the browser print dialog with print-optimized stylesheet (sidebar hidden, full-width content).
- **Per-file deploy status in sidebar** — each page in the sidebar shows a colored indicator reflecting the latest CI pipeline status: ● running, ✓ passed, ✗ failed. Status is fetched from the GitHub Actions / GitLab CI API.

---

## v1.1.0 — 2026-05-15

### Added

- **Offline drafts** — edits are saved to `localStorage` as you type. A restore/discard banner appears on reload if a draft is found.
- **Page history** — clock icon on each page opens the last 20 commits for that file. Any version can be restored with a single click (commits as a new revert commit).
- **Frontmatter support** — pages can declare `tags`, `author`, and `description` in YAML frontmatter. Tags render as clickable chips that filter the sidebar.
- **Wiki links `[[...]]`** — link any page by title with `[[Page Title]]` syntax. Case-insensitive resolution. Autocomplete dropdown in the editor when typing `[[`.
- **Full-text search via search.json** — ⌘K / Ctrl+K opens a search modal that queries a pre-built `search.json` index committed to the repo by CI.
- **Drag-and-drop image upload** — drop an image onto the editor; WikiNest uploads it to the repo via API and inserts the Markdown image tag at the cursor.

---

## v1.0.0 — 2026-05-13

### Added

- First public release.
- **Split-view editor** — Markdown editor with live rendered preview side-by-side.
- **Ctrl+S / ⌘S** to save (commit) the current page.
- **Sidebar tree** — collapsible folder tree listing all pages in `docs/`.
- **Folder support** — unlimited nesting; folders displayed from filesystem structure.
- **Basic search** — sidebar filter by page title.
- **PAT encryption** — Personal Access Token encrypted with a user password before `localStorage` storage.
- **GitHub Actions CI badge** — commit status visible in the UI.
- **GitHub support** — full read/write via GitHub REST API.
