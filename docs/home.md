---
description: "WikiNest — the wiki that lives in your repo. No server, no database, just Markdown and Git."
---

# WikiNest

**Your team's knowledge base, version-controlled and always in sync.**

WikiNest turns a plain `docs/` folder in your GitHub or GitLab repository into a beautiful, fully-featured wiki — with a split-view editor, full-text search, page history, and more. Every edit is a commit. No server required.

---

## Why WikiNest?

| | |
|---|---|
| 📝 | **Split-view editor** with a 16-button markdown toolbar |
| 🔗 | **Wiki links** — type `[[Page Name]]` to link pages with autocomplete |
| 🔍 | **Full-text search** across all pages (⌘K / Ctrl+K) |
| 🕐 | **Page history** — browse the last 20 commits and restore any version |
| 🏷️ | **Frontmatter** — tags, author, description with clickable tag chips |
| 🖼️ | **Drag-and-drop image upload** directly in the editor |
| 📴 | **Offline drafts** — edits survive page reloads until you're ready to save |
| 🌐 | **GitHub & GitLab** support with PAT encryption |
| 🎨 | **Dark mode** and responsive mobile layout |
| 🌍 | **i18n** — English and Russian, easily extensible |

---

## Navigate the docs

| Section | Description |
|---|---|
| [[Installation]] | Get WikiNest running in under 5 minutes |
| [[Configuration]] | Config options, PAT setup, GitHub Actions |
| [[Features]] | Full feature reference with shortcuts and syntax |
| [[Markdown reference]] | All supported Markdown: tables, code, callouts, and more |
| [[Feature Playground]] | Interactive demo page — try the editor features live |
| [[Changelog]] | What's new in each version |

---

## How it works

```
Browser → GitHub/GitLab API → commit to docs/ → CI pipeline → Pages deploy
```

1. You write Markdown in the split-view editor
2. Hit **Save** (Ctrl+S / ⌘S) — WikiNest commits directly to your repo via API
3. GitHub Actions / GitLab CI picks up the commit and deploys to Pages
4. The deploy status indicator in the sidebar shows ● / ✓ / ✗ in real time

---

## Try it now

> **Get started in seconds:**
>
> - 🚀 Click **⚙** in the top-right corner and enter your repo details and token
> - ✏️ Open [[Feature Playground]] and click **Edit** to try the editor live
> - 🔍 Press **⌘K** to search across all pages instantly
> - 🕐 Click the **clock icon** on any page to browse its full commit history
