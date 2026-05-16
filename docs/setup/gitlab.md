---
tags: [setup, gitlab]
description: "Step-by-step guide for deploying WikiNest on GitLab."
---

# GitLab Setup

This guide walks through deploying WikiNest using GitLab as your backend. For GitHub, see [[Installation]].

---

## Prerequisites

- A GitLab account (gitlab.com or self-hosted)
- A GitLab Personal Access Token with **`api`** and **`write_repository`** scopes

---

## Steps

### 1. Fork the repository

Go to the WikiNest repository on GitLab and click **Fork**. Choose your namespace and confirm. GitLab will create `https://gitlab.com/<you>/wikinest`.

### 2. Add the CI/CD variable

WikiNest's pipeline needs a token to build the `search.json` index and deploy to GitLab Pages.

1. In your fork, go to **Settings → CI/CD → Variables**
2. Click **Add variable**
3. Set **Key** to `GITLAB_TOKEN`
4. Set **Value** to your Personal Access Token
5. Uncheck **Protect variable** (unless you only want it on protected branches)
6. Click **Add variable**

> Your token needs `api` scope (to read pipeline status) and `write_repository` scope (to commit search index updates).

### 3. Edit config.json

In your fork, open `config.json` at the root of the repository and update it:

```json
{
  "provider": "gitlab",
  "owner": "your-gitlab-username",
  "repo": "wikinest",
  "branch": "main",
  "docsPath": "docs",
  "lang": "en"
}
```

Commit the change directly in the GitLab web editor or clone locally and push.

### 4. Wait for the pipeline

After the commit, go to **CI/CD → Pipelines** in your fork. The first pipeline takes about 1 minute to:

- Build the `search.json` index
- Deploy static files to GitLab Pages

A green checkmark means the deploy succeeded.

### 5. Open the wiki and configure your token

GitLab Pages URLs follow the pattern:

```
https://<your-username>.gitlab.io/wikinest/
```

> Note: this differs from GitHub Pages (`https://<username>.github.io/wikinest/`). If your GitLab instance uses a custom domain, check **Settings → Pages** for the exact URL.

Open the URL, click the **⚙** icon in the top-right, and enter:

- **Owner** — your GitLab username (matches `config.json`)
- **Repo** — `wikinest`
- **Token** — your GitLab PAT
- **Password** — a password of your choice (used to encrypt the token in `localStorage`)

Click **Save**. WikiNest will verify the connection and load your `docs/` tree.

---

## Troubleshooting

**Pipeline fails on first run** — check that `GITLAB_TOKEN` is set and has `write_repository` scope. The pipeline needs to commit `search.json` back to the repo.

**Pages not found (404)** — GitLab Pages may take a few minutes after the first successful pipeline. Also confirm the Pages feature is enabled under **Settings → General → Visibility, project features, permissions**.

**Cannot save pages** — confirm the token you entered in the wiki settings has `write_repository` scope. `read_api`-only tokens can read but not commit.
