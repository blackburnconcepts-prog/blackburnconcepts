# Blackburn Concepts — Deployment Guide
## blackburnconcepts.ca

---

## FOLDER STRUCTURE

```
blackburnconcepts/          ← root of your GitHub repo
│
├── index.html              ← main website (self-contained, all images embedded)
├── CNAME                   ← tells GitHub Pages your domain (DO NOT EDIT)
├── robots.txt              ← search engine instructions
├── sitemap.xml             ← search engine sitemap
├── 404.html                ← custom error page
│
├── images/                 ← (optional) for future image swaps
│   ├── og-image.jpg        ← social share preview (1200×630px recommended)
│   └── favicon.png         ← browser tab icon (512×512px recommended)
│
└── DEPLOYMENT.md           ← this file
```

> NOTE: The current index.html is fully self-contained.
> All 135 photos are base64-embedded. No separate image files needed to run the site.

---

## STEP 1 — CREATE A GITHUB ACCOUNT

1. Go to https://github.com
2. Sign up for a free account if you don't have one
3. Confirm your email address

---

## STEP 2 — CREATE THE REPOSITORY

1. Click the **+** button (top right) → **New repository**
2. Repository name: `blackburnconcepts`  
   *(or any name — it won't affect your domain)*
3. Set visibility to **Public**
4. Do NOT initialize with README
5. Click **Create repository**

---

## STEP 3 — UPLOAD YOUR FILES

### Option A — Drag and Drop (easiest)
1. Open your new repository
2. Click **Add file** → **Upload files**
3. Drag ALL these files into the window:
   - `index.html`
   - `CNAME`
   - `robots.txt`
   - `sitemap.xml`
   - `404.html`
4. Scroll down → click **Commit changes**

### Option B — GitHub Desktop App
1. Download GitHub Desktop: https://desktop.github.com
2. Sign in with your GitHub account
3. Clone your new repository to your computer
4. Copy all files into the cloned folder
5. In GitHub Desktop: write a commit message → click **Commit to main** → **Push origin**

### Option C — Git command line
```bash
git init
git remote add origin https://github.com/YOUR_USERNAME/blackburnconcepts.git
git add .
git commit -m "Initial deployment"
git branch -M main
git push -u origin main
```

---

## STEP 4 — ENABLE GITHUB PAGES

1. Go to your repository on GitHub
2. Click **Settings** (top menu)
3. In the left sidebar → **Pages**
4. Under **Source**: select **Deploy from a branch**
5. Branch: **main** / folder: **/ (root)**
6. Click **Save**
7. GitHub will show: *"Your site is published at https://YOUR_USERNAME.github.io/blackburnconcepts"*

---

## STEP 5 — CONNECT YOUR DOMAIN (blackburnconcepts.ca)

### 5A — Add domain in GitHub Pages settings
1. In **Settings → Pages**
2. Under **Custom domain**: type `blackburnconcepts.ca`
3. Click **Save**
4. *(The CNAME file handles this automatically — it should already be set)*

### 5B — Update DNS at your domain registrar

Log in to wherever you registered **blackburnconcepts.ca**
*(e.g. GoDaddy, Namecheap, Google Domains, Wix, etc.)*

**Delete any existing A records or CNAME records for @ and www**

Then add these new records:

#### A Records (point @ to GitHub)
| Type | Name | Value | TTL |
|------|------|-------|-----|
| A | @ | 185.199.108.153 | 3600 |
| A | @ | 185.199.109.153 | 3600 |
| A | @ | 185.199.110.153 | 3600 |
| A | @ | 185.199.111.153 | 3600 |

#### CNAME Record (point www to GitHub)
| Type | Name | Value | TTL |
|------|------|-------|-----|
| CNAME | www | YOUR_USERNAME.github.io | 3600 |

> Replace `YOUR_USERNAME` with your actual GitHub username

#### Wait for propagation
DNS changes take **15 minutes to 48 hours** to propagate worldwide.
You can check status at: https://dnschecker.org

---

## STEP 6 — ENABLE HTTPS (SSL)

1. After DNS propagates, go back to **Settings → Pages**
2. Check the box: **Enforce HTTPS**
3. Your site will be live at: **https://blackburnconcepts.ca** ✓

---

## IF YOUR DOMAIN IS CURRENTLY ON WIX

If blackburnconcepts.ca is connected to a Wix site:

1. Log into your **domain registrar** (not Wix — the place you originally bought the domain)
2. If you bought the domain THROUGH Wix, go to: Wix Dashboard → Domains → Manage
3. Find the DNS settings and update the A records and CNAME as shown above
4. In Wix dashboard, disconnect the domain from your Wix site first

---

## STEP 7 — ADD A FAVICON (Optional but recommended)

1. Create a 512×512px PNG of the Blackburn Concepts flame logo
2. Name it `favicon.png`
3. Upload it to your repository
4. Add this line inside the `<head>` of index.html (before `</head>`):
```html
<link rel="icon" type="image/png" href="/favicon.png">
<link rel="apple-touch-icon" href="/favicon.png">
```

---

## STEP 8 — ADD OG IMAGE (Social share preview)

When you share the URL on Instagram, iMessage, etc., it shows a preview image.

1. Create a 1200×630px JPEG of the shop/car (cinematic shot)
2. Name it `og-image.jpg`
3. Upload to repository
4. The meta tag is already in index.html:
   `<meta property="og:image" content="https://blackburnconcepts.ca/og-image.jpg">`

---

## UPDATING THE WEBSITE

To update content after going live:

1. Edit `index.html` locally
2. Upload the new version to GitHub (drag & drop → commit)
3. GitHub Pages auto-deploys in ~60 seconds

---

## TROUBLESHOOTING

| Problem | Solution |
|---------|----------|
| Site shows 404 after enabling Pages | Wait 5 mins, hard refresh (Ctrl+Shift+R) |
| Domain not connecting | DNS hasn't propagated yet — wait up to 48h |
| HTTPS not working | Wait for DNS, then check Enforce HTTPS in Settings → Pages |
| Site shows old version | Hard refresh browser (Ctrl+Shift+R / Cmd+Shift+R) |
| Custom domain keeps resetting | Make sure CNAME file is in your repo |

---

## CONTACT

blackburn.concepts@gmail.com  
647 325 6130  
325 Weston Rd. Unit D3, Toronto, ON

