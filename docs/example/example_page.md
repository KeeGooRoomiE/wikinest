---
tags: [demo, playground]
author: WikiNest Team
description: "An interactive showcase of WikiNest-specific features — wiki links, frontmatter, and markdown."
---

# Feature Playground

This page demonstrates WikiNest-specific features in action. Everything you see here — the tags above, the author attribution, the links below — is rendered from plain Markdown with a YAML frontmatter block at the top of the file. Open this page in the editor to see (and try) everything.

---

## Wiki links

Wiki links let you reference any page by its title using double brackets. They resolve case-insensitively, so `[[features]]` and `[[Features]]` go to the same page.

Start exploring from the [[Home]] page, check the complete [[Features]] list, or look up syntax in the [[Markdown reference]]. In the editor, typing `[[` opens an autocomplete dropdown — start typing a page title and press Enter to insert the link.

Wiki links are first-class citizens in WikiNest: they show up in search, they highlight broken links (pointing to pages that don't exist yet), and they're as easy to write as `[[Page Name]]`.

---

## Frontmatter

The block at the very top of this file (before the `# Feature Playground` heading) is YAML frontmatter. WikiNest reads three fields:

```yaml
---
tags: [demo, playground]
author: WikiNest Team
description: "An interactive showcase of WikiNest-specific features."
---
```

| Field | What it does |
|---|---|
| `tags` | Rendered as clickable chips below the page title; clicking a tag filters the sidebar |
| `author` | Shown in the page header next to the last-edited timestamp |
| `description` | Used in search result previews |

All three fields are optional. Pages without frontmatter still work perfectly.

---

## Try the editor

Open this page in edit mode and work through the checklist:

- [ ] Open this page in the editor (click **Edit** above)
- [ ] Use the toolbar to make text **bold** or _italic_
- [ ] Try **Ctrl+S** / **⌘S** to save
- [ ] Drop an image file onto the editor textarea
- [ ] Type `[[` to trigger wiki link autocomplete
- [ ] Click the **clock icon** to see this page's commit history
- [ ] Press **⌘K** to search across all pages

---

## Markdown showcase

### Table

| Feature | Shortcut | Since |
|---|---|---|
| Save | Ctrl+S / ⌘S | v1.0.0 |
| Search | Ctrl+K / ⌘K | v1.1.0 |
| Page history | Clock icon | v1.1.0 |
| Print | Print icon | v1.2.0 |

### Blockquote

> "Documentation is a love letter that you write to your future self."
>
> — Damian Conway

### Code block

```javascript
// WikiNest resolves wiki links by title at render time
function resolveWikiLink(title, pages) {
  return pages.find(p =>
    p.title.toLowerCase() === title.toLowerCase()
  );
}
```

### Nested list

- Editor
  - Split-view (edit + preview)
  - 16-button toolbar
  - Offline drafts
- Navigation
  - Sidebar folder tree
  - Wiki links with autocomplete
  - Full-text search (⌘K)
- History
  - Last 20 commits per page
  - One-click restore

---

Back to [[Home]]
