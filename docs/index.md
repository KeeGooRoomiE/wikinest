---
tags: [overview]
description: "What WikiNest is and how to find your way around this wiki."
---

# Welcome to WikiNest

WikiNest is a git-native wiki: your documentation lives in the `docs/` folder of a GitHub or GitLab repository. Every page is a Markdown file. Every save is a commit. There is no separate server, no database, and no sync to worry about — the repo *is* the wiki.

## How pages work

Each `.md` file inside `docs/` becomes a page in the sidebar. The file path maps directly to the URL:

| File | Sidebar path |
|---|---|
| `docs/index.md` | Home / index |
| `docs/setup/installation.md` | Setup → Installation |
| `docs/reference/markdown.md` | Reference → Markdown reference |

Folders group related pages. A folder can have a custom display name stored in its `_meta.json` file (editable from the sidebar with the pencil icon).

## Editing a page

1. Navigate to any page in the sidebar
2. Click **Edit** — the split-view editor opens with a live Markdown preview
3. Use the 16-button toolbar or type Markdown directly
4. Press **Ctrl+S** / **⌘S** (or click **Save**) to commit the change

Unsaved edits are kept as offline drafts so you never lose work on a reload.

## Finding things

- **Sidebar tree** — browse pages by folder
- **⌘K / Ctrl+K** — full-text search across all pages
- **Wiki links** — `[[Page Name]]` links anywhere in a page open the target instantly

## Where to go next

| | |
|---|---|
| First time? | [[Installation]] then [[Configuration]] |
| Exploring features | [[Features]] and [[Feature Playground]] |
| Markdown syntax | [[Markdown reference]] |
| What changed? | [[Changelog]] |
