# Deploying to GitHub Pages

This project is pre-configured to deploy to `www.knightangels.ng` via GitHub
Pages. `public/CNAME` and the `homepage` field in `package.json` are already
set for that domain.

## 1. Push to GitHub

```bash
npm install
git init
git add .
git commit -m "Initial commit: Knight Angels site"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/knight-angels.git
git push -u origin main
```

## 2. Deploy

```bash
npm run deploy
```

This builds the site and pushes `dist/` (including `CNAME`) to a `gh-pages`
branch.

## 3. Enable Pages

In the GitHub repo: **Settings → Pages → Source → Deploy from a branch →
`gh-pages` / root** → Save.

## 4. Point your domain at GitHub

At your DNS registrar for `knightangels.ng`:

| Type | Host | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | YOUR_USERNAME.github.io |

DNS propagation can take anywhere from a few minutes to 24+ hours.

## 5. Enforce HTTPS

Back in **Settings → Pages**, once the domain is verified, check
**Enforce HTTPS**. GitHub issues the certificate automatically once DNS is
correctly pointed — this can take a little while after the domain first
verifies.

## Redeploying after changes

Any time you update the site:

```bash
npm run deploy
```

`gh-pages` handles rebuilding and re-pushing automatically.

## Using a different domain later

If you move off `knightangels.ng`, update `public/CNAME` (or delete it for
the default `username.github.io/knight-angels/` URL — in that case also set
`base: '/knight-angels/'` in `vite.config.js`).
