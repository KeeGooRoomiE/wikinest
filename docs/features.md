---
tags: [reference, features]
author: WikiNest Team
description: "Complete reference for all WikiNest features, grouped by category."
---

# Features

Complete reference for everything WikiNest can do. See also [[Markdown reference]] for Markdown syntax and [[Configuration]] for setup options.

---

## Editor

**Split-view editor** — pages open in a two-pane layout: raw Markdown on the left, rendered preview on the right. The preview updates as you type.

**16-button toolbar** — one-click insertion for: Bold, Italic, Strikethrough, Heading, Link, Image, Blockquote, Code, Code block, Unordered list, Ordered list, Task list, Table, Horizontal rule, Wiki link, and Tags/Frontmatter.

**Keyboard shortcuts**

| Shortcut | Action |
|---|---|
| Ctrl+S / ⌘S | Save (commit) |
| Ctrl+B / ⌘B | Bold |
| Ctrl+I / ⌘I | Italic |
| ⌘K | Open full-text search |

**Drag-and-drop image upload** — drop any image file onto the editor textarea. WikiNest uploads it to the repo and inserts the Markdown image tag at the cursor position automatically.

**Offline drafts** — edits are auto-saved to `localStorage` as you type. If you close the tab or reload, a banner offers to restore or discard the draft. Drafts are per-page.

---

## Navigation

**Sidebar tree** — all pages in `docs/` are listed in a collapsible folder tree. Folder display names are configurable (see Folder renaming below).

**Folder display-name rename** — hover any folder in the sidebar to reveal a pencil icon. Click it to type a custom display name; WikiNest writes the value to `_meta.json` in that folder and commits it.

**Wiki links** — type `[[Page Title]]` anywhere in Markdown. WikiNest resolves links by page title (case-insensitive). In the editor, typing `[[` opens an autocomplete dropdown of all page titles.

**Table of contents** — for pages with headings, a "On this page" TOC appears in the sidebar. Can be toggled in Display preferences.

---

## Search

**Full-text search (⌘K)** — press ⌘K or Ctrl+K to open the search modal. WikiNest searches across all page content using a pre-built `search.json` index. Results show matching lines with context.

---

## History

**Page history** — click the clock icon on any page to open its commit history (up to the last 20 commits). Each entry shows the commit message, author, and date.

**Restore version** — click **Restore** next to any historical version to revert the page to that content. The restore is committed to the repo as a new commit.

---

## Frontmatter

Pages can have YAML frontmatter at the top:

```yaml
---
tags: [setup, guide]
author: Your Name
description: "A short description of this page."
---
```

- **tags** — rendered as clickable chips below the page title. Clicking a tag filters the sidebar to pages with that tag.
- **author** — displayed in the page header next to the last-edited date.
- **description** — used in search results and page previews.

---

## Deploy status

**Per-file deploy status indicator** — the sidebar shows a colored dot next to each page:

| Indicator | Meaning |
|---|---|
| ● (yellow) | Pipeline running |
| ✓ (green) | Deployed successfully |
| ✗ (red) | Pipeline failed |

Status is pulled from the GitHub Actions / GitLab CI API using your configured token.

---

## Authentication

**PAT encryption** — your Personal Access Token is encrypted with a user-chosen password before being stored in `localStorage`. The password is required once per session.

**GitHub support** — configure `provider: "github"` with a token that has `repo` scope. See [[Installation]].

**GitLab support** — configure `provider: "gitlab"` with a token that has `api` + `write_repository` scope. See [[GitLab Setup]].

---

## Print / PDF

Click the **print icon** (or use the Display preferences menu) to open the browser's print dialog. The page stylesheet includes print-optimized styles: sidebar hidden, full-width content, clean typography.

---

## Display preferences

The Display preferences panel (accessible from the toolbar) controls:

| Preference | Description |
|---|---|
| Show table of contents | Toggle the "On this page" sidebar TOC |
| Split preview | Toggle between split-view and edit-only mode |

Preferences are saved per-browser in `localStorage`.

---

## Dark mode

WikiNest respects the OS-level `prefers-color-scheme` setting and also provides a manual toggle in the header. The selection is saved in `localStorage`.

---

## Mobile

The layout is responsive. On narrow screens the sidebar collapses to a hamburger menu and the editor switches to single-pane mode (edit or preview, not both).

---

## Internationalization (i18n)

All UI labels are loaded from `i18n/<lang>.json`. The language can be switched from the header dropdown. See [[Internationalization]] for how to add a new language.

Currently supported: **English** (`en`), **Russian** (`ru`).
