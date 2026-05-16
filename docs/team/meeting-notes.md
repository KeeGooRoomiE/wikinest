---
tags: [team, meetings]
author: Team Lead
description: "Weekly sync notes — latest first."
---

# Meeting Notes

Weekly engineering sync — notes kept in reverse chronological order. Add new entries at the top.

---

## 2026-05-15 — Weekly Sync

**Attendees:** Alex R., Sam C., Priya M., Jordan K., (Dana L. — async)

### Decisions

- **Ship v1.2.0 today** — toolbar and deploy status features are stable; changelog is written and reviewed.
- **Folder rename** will go out in the next release (Unreleased) — needs one more round of QA on the `_meta.json` commit path.
- **GitLab docs** to be written alongside the GitLab setup work (assigned to Sam).

### Action items

- [x] Alex — cut v1.2.0 tag and monitor pipeline
- [ ] Sam — write [[GitLab Setup]] docs page and test end-to-end on gitlab.com
- [ ] Priya — QA folder rename on Firefox and Safari
- [ ] Jordan — add rollback test case to [[Deploy Runbook]]
- [ ] Dana — update `i18n/ru.json` with new keys from v1.2.0

### Notes

- Deploy status polling uses a 30s interval; Alex flagged we might hit rate limits for repos with high commit frequency. Will monitor in production.
- Discussed whether to support `[[Page Name|Alias]]` syntax for wiki links — deferred to backlog.
- Dark mode flash-of-unstyled-content on initial load is a known issue; Jordan has a fix in draft.

---

## 2026-05-08 — Weekly Sync

**Attendees:** Alex R., Sam C., Priya M., Jordan K., Dana L.

### Decisions

- **Freeze feature scope for v1.2.0** — only toolbar expansion, display prefs, print, and deploy status go in this release.
- **Offline drafts confirmed working** on Chrome, Firefox, Safari — ship as stable in v1.1.0 notes.
- Drop the idea of server-side search for now; `search.json` approach is fast enough for wikis under ~500 pages.

### Action items

- [x] Alex — merge offline drafts PR (#41) and page history PR (#43)
- [x] Jordan — wire up frontmatter tag chips to sidebar filter
- [x] Sam — implement `[[...]]` autocomplete in the editor
- [x] Priya — write end-to-end tests for wiki link resolution
- [ ] Dana — translate new frontmatter UI strings to RU (carried forward)

### Notes

- `search.json` is now rebuilt on every push by CI; build adds ~8s to pipeline.
- Discussed image storage: images go into `docs/assets/` by default. Users can change the path in `config.json`. No external CDN needed.
- v1.1.0 release candidate looks clean. Plan to tag on 2026-05-15.

---

## 2026-05-01 — Weekly Sync

**Attendees:** Alex R., Sam C., Priya M.  _(Jordan + Dana — OOO)_

### Decisions

- **Start v1.1.0 sprint** — priority features: wiki links, page history, frontmatter, drag-drop upload.
- Adopt YAML frontmatter (not TOML) to stay consistent with popular static-site generators.
- PAT encryption approach (AES-GCM in `localStorage`) confirmed with security review — no changes needed.

### Action items

- [x] Alex — spike wiki link resolution (title-based, case-insensitive)
- [x] Sam — implement GitHub Commits API integration for page history
- [x] Priya — design frontmatter schema (tags / author / description)
- [ ] Alex — set up `search.json` CI build step (moved to next sprint)

### Notes

- v1.0.0 shipped cleanly. Three external users already using it; positive feedback on the split-view editor.
- Biggest complaint from early users: no way to link between pages. Wiki links are now highest priority.
- GitHub rate limits: authenticated requests give 5,000 req/hr — more than enough for the commit history feature.
