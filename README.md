# DataForge Site — Setup & Deploy Guide

## Stack
- **Framework**: Astro (static output)
- **Hosting**: GitHub Pages (free)
- **Domain**: Namecheap (~$10–13/yr)
- **Deploy**: Push to `main` → auto-deploys via GitHub Actions

---

## Local Dev Setup

```bash
# 1. Navigate into the project
cd dataforge-astro

# 2. Install dependencies
npm install

# 3. Start dev server
npm run dev
# → http://localhost:4321
```

---

## GitHub Setup (one-time)

1. Create a new repo on GitHub: `dataforge-site` (or any name)
2. Push this project:
   ```bash
   git init
   git add .
   git commit -m "init: DataForge site"
   git remote add origin https://github.com/YOURUSERNAME/dataforge-site.git
   git push -u origin main
   ```
3. In GitHub repo → **Settings → Pages**
   - Source: **GitHub Actions**
   - That's it. First deploy triggers automatically.

---

## Custom Domain Setup (Namecheap)

1. Buy domain at namecheap.com
2. In GitHub repo → Settings → Pages → Custom Domain → enter your domain
3. GitHub will show 4 IP addresses — add them as **A records** in Namecheap DNS:
   ```
   185.199.108.153
   185.199.109.153
   185.199.110.153
   185.199.111.153
   ```
4. Also add a **CNAME record**: `www` → `YOURUSERNAME.github.io`
5. Check "Enforce HTTPS" in GitHub after DNS propagates (~10 min)
6. In `astro.config.mjs`, update `site` to your real domain and remove the `base` line.

---

## File Structure

```
dataforge-astro/
├── src/
│   ├── layouts/
│   │   └── Layout.astro       ← Nav + footer wrapper
│   ├── pages/
│   │   ├── index.astro        ← Homepage ✅
│   │   ├── services.astro     ← Next to build
│   │   ├── portfolio.astro    ← Next to build
│   │   ├── about.astro        ← Next to build
│   │   └── contact.astro      ← Next to build
│   └── styles/
│       └── global.css         ← Full design system
├── public/                    ← Static assets (favicon, images)
├── astro.config.mjs
└── package.json
```

---

## Pages Remaining

| Page | Status |
|------|--------|
| Home (index) | ✅ Done |
| Services + Pricing | Next session |
| Portfolio / Case Studies | Next session |
| About | Next session |
| Contact | Next session |

---

## Design Tokens (quick reference)

| Token | Value |
|-------|-------|
| `--accent` | `#E8920A` (amber) |
| `--bg` | `#070707` |
| `--text` | `#F0EAE0` |
| `--muted` | `#6A6560` |
| Display font | Barlow Condensed |
| Body font | DM Sans |
| Mono font | JetBrains Mono |

---

## Email

Update `hello@dataforgewichita.com` throughout once your domain is live.
Consider Forwardemail.net for free email forwarding from your domain to Gmail.
