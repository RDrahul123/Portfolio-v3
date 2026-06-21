# Portfolio + Back Office — Setup Guide

This package has four files that must live **in the same folder** of your GitHub repository (the repo you publish with GitHub Pages):

```
your-repo/
├── index.html       ← the public portfolio
├── admin.html        ← the back office (hidden, login-protected)
├── content.json      ← all editable content (text, links, projects, etc.)
└── favicon.svg        ← the browser-tab icon
```

## 1. Upload the files

Upload `index.html`, `admin.html`, `content.json`, and `favicon.svg` to the root of your GitHub Pages repository (e.g. `RDrahul123/Portfolio-v2`), replacing the old `index.html`. Commit and push.

## 2. Enable GitHub Pages (if not already)

Repo → Settings → Pages → Source: branch `main`, folder `/ (root)`. Your site will be live at:
`https://<username>.github.io/<repo-name>/`

## 3. Create a GitHub Personal Access Token (so the back office can publish)

The back office edits content **in your browser**, then pushes the updated `content.json` straight to your GitHub repo using GitHub's API. For that, it needs a token.

1. Go to **GitHub → Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token**
2. Give it a name like `portfolio-admin`
3. **Repository access:** select "Only select repositories" → choose your portfolio repo only
4. **Permissions:** under "Repository permissions," set **Contents: Read and write**
5. Set an expiration (e.g. 90 days or 1 year — you'll need to regenerate it after it expires)
6. Generate, then **copy the token** (starts with `github_pat_...`) — GitHub only shows it once

## 4. Log in to the back office

Visit `https://<username>.github.io/<repo-name>/admin.html` directly, or from the live portfolio:
- Click the site logo (top-left) **5 times quickly**, or
- Go to `index.html#admin`

**Login credentials:**
- Username: `prakrit3625`
- Password: `prakrit@3625`

## 5. Connect GitHub (one-time setup)

In the back office, open **⚙ GitHub Settings** and fill in:
- **GitHub Repository:** `username/repository-name` (e.g. `RDrahul123/Portfolio-v2`)
- **Branch:** `main` (or whatever your default branch is)
- **content.json Path:** `content.json` (leave as-is unless you moved the file)
- **Token:** paste the token from step 3

Click **Save Connection Settings**, then **Test Connection** to confirm it works. This token is stored only in your browser's local storage — it is never sent anywhere except directly to GitHub.

## 6. Edit and publish

Use the sidebar to edit Hero, About, Experience, Projects, Skills, Resume, Contact, and Footer. When you're happy with your changes, click **🚀 Save & Publish** at the bottom. This commits the updated `content.json` straight to your GitHub repo.

GitHub Pages typically rebuilds within 30–90 seconds. Refresh your live portfolio to see the changes.

## Notes

- **Security:** This is a client-side-only admin panel — the username/password gate is a deterrent for casual visitors, not a substitute for proper auth. Because the token lives in your browser's storage, only use the back office on a device/browser you trust, and avoid logging in on shared/public computers. If you ever suspect the token leaked, revoke it immediately in GitHub settings and generate a new one.
- **Token expiration:** When your token expires, just generate a new one and paste it into GitHub Settings again — your repo/branch/path settings stay saved.
- **Multiple devices:** Settings (repo, branch, token) are stored per-browser. If you use the back office on a new device, you'll need to re-enter GitHub Settings there too.
- **Reload from GitHub:** If you've published changes elsewhere or want to discard unsaved edits, use **↻ Reload from GitHub** to pull the latest version.
