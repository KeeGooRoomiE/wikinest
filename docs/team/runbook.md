---
tags: [ops, runbook]
author: Ops Team
description: "Step-by-step procedure for deploying WikiNest to production."
---

# Deploy Runbook

**Service:** WikiNest wiki  
**Repo:** `github.com/your-org/wikinest`  
**Pages URL:** `https://your-org.github.io/wikinest/`  
**Last reviewed:** 2026-05-16

---

## Pre-flight checklist

Complete every item before starting the deploy:

- [ ] All PRs for this release are merged to `main`
- [ ] `docs/changelog.md` is updated with the new version and date
- [ ] `config.json` version field is bumped (if applicable)
- [ ] No open pipeline failures on `main`
- [ ] At least one other team member has reviewed the diff
- [ ] Rollback commit SHA is noted (run `git log -1 --format="%H" origin/main`)

---

## Deploy procedure

### 1. Pull latest main

```bash
git checkout main
git pull origin main
```

### 2. Verify the build locally (optional but recommended)

```bash
# Regenerate search index
node scripts/build-search.js

# Check output
cat search.json | python3 -m json.tool > /dev/null && echo "search.json OK"
```

### 3. Tag the release

```bash
git tag -a v1.2.0 -m "Release v1.2.0"
git push origin v1.2.0
```

### 4. Monitor the pipeline

Open **Actions → Deploy** in GitHub (or **CI/CD → Pipelines** in GitLab) and watch for the pipeline triggered by the tag push.

```
Expected duration: ~60–90 seconds
Expected result:   ✓ All steps green
```

### 5. Smoke test

After the pipeline completes:

1. Open `https://your-org.github.io/wikinest/`
2. Confirm the sidebar loads (page tree visible)
3. Open any page — confirm content renders
4. Press ⌘K — confirm search returns results
5. Check the deploy status indicator (●/✓/✗) in the sidebar

### 6. Announce

Post in `#releases` Slack channel:

```
WikiNest v1.2.0 is live 🚀
https://your-org.github.io/wikinest/
See changelog for what's new.
```

---

## Rollback procedure

If the deploy causes issues, revert to the previous good commit:

```bash
# Find the last known-good SHA
git log --oneline -10 origin/main

# Revert (creates a new commit — safe for shared branches)
git revert <bad-commit-sha> --no-edit
git push origin main
```

Wait for the pipeline to re-run (~60s). Verify the rollback with the smoke test above.

If the revert is not sufficient and you need to hard-reset the Pages deploy, re-run the last successful pipeline manually from the Actions / CI UI.

---

## Common failure modes

| Symptom | Likely cause | Fix |
|---|---|---|
| Pipeline fails at "build search index" | `GITHUB_TOKEN` / `GITLAB_TOKEN` missing or expired | Rotate the token in repo secrets/variables |
| Pages shows 404 after deploy | Pages not enabled or deploy job skipped | Enable Pages in repo settings; re-run pipeline |
| Sidebar empty after deploy | `search.json` not committed | Check pipeline logs; run `node scripts/build-search.js` locally and push |
| Save fails for all users | PAT scopes insufficient | Re-issue PAT with `repo` (GitHub) or `write_repository` (GitLab) scope |
| Deploy status stuck at ● | API rate limit hit | Wait ~1 min; check rate limit headers in browser network tab |

---

## Contacts

| Role | Name | Contact |
|---|---|---|
| On-call ops | Alex Rivera | `@alex` in Slack / alex@example.com |
| Backup on-call | Sam Chen | `@sam` in Slack |
| Escalation | Engineering lead | `#oncall` Slack channel |
| GitLab admin | IT Ops | `it-ops@example.com` |

For production incidents, page the on-call via `#oncall` and open an incident in the team tracker.
