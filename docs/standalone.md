# WikiNest Standalone

---
tags: [enterprise, standalone]
description: Enterprise version of WikiNest with a Python backend, RBAC, and AI assistant — deployed on your own infrastructure.
---

WikiNest Standalone is the enterprise edition of WikiNest. It keeps the same zero-friction editing experience and git-as-storage principle, but adds a Python backend, server-side access control, and an AI assistant layer — all running on your own server.

> **Interested?** Contact [@KeeGooRoomiE](https://github.com/KeeGooRoomiE) to discuss setup and licensing.

---

## How it differs from WikiNest

| | WikiNest (open source) | WikiNest Standalone |
|---|:---:|:---:|
| Backend | None — Git API only | Python + FastAPI |
| Auth | Single shared password | Server sessions + RBAC |
| Permissions | All editors see everything | Per-document, per-folder |
| Hosting | GitHub / GitLab Pages | Your VM / Docker |
| AI assistant | — | RAG over your docs |
| Telegram integration | — | Built-in |
| Word import | — | `.docx` → Markdown |
| Save latency | CI pipeline (seconds) | Instant (direct disk write) |

---

## Own infrastructure — your data stays yours

WikiNest (open source) runs entirely through GitHub or GitLab — your content lives on third-party servers.

Standalone deploys on your VM with a single `docker compose up -d --build`. Three containers: wiki frontend, Python API, Caddy with automatic TLS. Content, passwords, and history never leave your server.

---

## Real RBAC instead of a shared password

The open-source version uses a single edit password checked in the browser.

Standalone has server-side sessions with assignable roles: `admin`, `editor`, `viewer`, or any custom role you define. Permissions cascade from folders down to individual documents. A user who doesn't have access to a page cannot fetch it — the server returns 403 before the content is served.

---

## AI assistant over your knowledge base

A separate `backend_rag` service indexes your entire documentation and connects it to an LLM (OpenAI or Anthropic). Staff ask questions in plain language. The system retrieves relevant documents, filters results to what the requester's role can see, and returns an answer with a direct link to the source page.

Vision-capable models also handle screenshots and diagrams embedded in your docs.

**RBAC applies before the LLM call** — documents outside the user's role are excluded from the search index before the query is sent. There is no prompt-level trick to surface restricted content.

---

## Telegram integration

The admin panel (`/admin.html`) generates one-time invite keys. An employee activates the key in the Telegram bot — their account is bound to a role. Revoking access is one click. No email setup, no SSO configuration required. Number of users is unlimited.

---

## Instant saves, no CI wait

Every save in open-source WikiNest goes through GitHub Actions — a pipeline run of seconds to minutes.

Standalone writes directly to disk via the Python backend, commits locally and synchronously, and optionally pushes to GitHub in the background as a backup. The page updates immediately after save.

---

## Word import

The `/api/write/convert_docx` endpoint accepts a `.docx` file, converts it to Markdown via python-docx, commits the result, and rebuilds the search index. Migrating existing documentation from Word does not require manual copy-paste.

---

## Git history as an audit log

Every change is a named commit with author role and timestamp — same as open-source WikiNest. The history button in the editor shows all versions; any version can be previewed or restored.

---

## Deployment

```bash
docker compose up -d --build
```

Three services start: wiki, RAG backend, Caddy reverse proxy with automatic TLS. Configuring a new client is: update `sections.json` (content structure), `roles.json` (permission rules), and the domain in `Caddyfile`.

No database. No Kubernetes. Content is git, services are three Docker containers.

---

> To discuss enterprise setup, contact [@KeeGooRoomiE](https://github.com/KeeGooRoomiE).
