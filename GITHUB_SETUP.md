# ChipKraft Website — GitHub Pages Setup Guide

## 📁 Project Structure

```
chipkraft-site/
├── index.html              ← Main website (homepage)
├── assets/
│   └── shared.css          ← Shared styles used by all blog pages
├── blog/
│   ├── index.html          ← Blog listing page (shows all posts + filters)
│   └── posts/
│       ├── template-post.html          ← COPY THIS to add a new blog post
│       ├── gan-power-electronics.html  ← Sample post 1
│       ├── wizard-vs-freeform.html     ← Sample post 2
│       └── surface-finish-guide.html  ← Sample post 3
└── GITHUB_SETUP.md         ← This file
```

---

## 🚀 Step 1: Deploy to GitHub Pages (One-Time Setup)

### 1.1 Create a GitHub Account
Go to https://github.com and create a free account if you don't have one.

### 1.2 Create a New Repository
1. Click **"New"** (green button) on your GitHub dashboard
2. Repository name: `chipkraft-site` (or any name you like)
3. Set it to **Public** (required for free GitHub Pages)
4. Click **"Create repository"**

### 1.3 Upload Your Files
**Option A — GitHub Web UI (easiest, no coding needed):**
1. Open your new repository
2. Click **"uploading an existing file"**
3. Drag and drop ALL files from the `chipkraft-site/` folder
4. Keep the folder structure intact (blog/ subfolder must stay inside)
5. Click **"Commit changes"**

**Option B — Git command line:**
```bash
cd chipkraft-site
git init
git add .
git commit -m "Initial commit — ChipKraft website"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/chipkraft-site.git
git push -u origin main
```

### 1.4 Enable GitHub Pages
1. Go to your repository on GitHub
2. Click **Settings** (top tab)
3. Scroll down to **"Pages"** in the left sidebar
4. Under "Source", select **"Deploy from a branch"**
5. Branch: **main** | Folder: **/ (root)**
6. Click **Save**

### 1.5 Your Site is Live!
After 1–2 minutes, your site will be live at:
```
https://YOUR_USERNAME.github.io/chipkraft-site/
```

---

## ✏️ Step 2: Edit Your Code Anytime

### Option A — Edit on GitHub.com (no software needed)
1. Go to your repository
2. Click on any file (e.g., `index.html`)
3. Click the **pencil icon** (Edit) in the top right
4. Make your changes
5. Click **"Commit changes"** at the bottom
6. Your site updates in ~60 seconds

### Option B — Edit Locally with VS Code (recommended)
1. Install [Visual Studio Code](https://code.visualstudio.com/) (free)
2. Install the **"Live Server"** extension in VS Code
3. Clone your repo: `git clone https://github.com/YOUR_USERNAME/chipkraft-site.git`
4. Open the folder in VS Code
5. Right-click `index.html` → **"Open with Live Server"** to preview locally
6. After editing, push changes:
   ```bash
   git add .
   git commit -m "Updated homepage hero text"
   git push
   ```

---

## 📝 Step 3: Add a New Blog Post (Anytime)

### 3.1 Copy the Template
In your project, go to `blog/posts/` and **copy** `template-post.html`.
Rename the copy to something descriptive, like:
```
my-new-blog-post.html
```

### 3.2 Edit the Post
Open your new file and fill in the ✏️ marked sections:
- **`<title>`** — Post title for browser tab and SEO
- **`<meta name="description">`** — SEO description (150–160 chars)
- **Breadcrumb category** — e.g., "Semiconductor" or "Tutorial"
- **`<span class="cat-badge">`** — Category badge text
- **`<h1>`** — Your post title
- **`.lead` paragraph** — Short intro sentence
- **Date and read time** in `.post-meta-bar`
- **Article body** — Write your content using h2/h3/p/ul/blockquote
- **Table of Contents** in sidebar — Update links to your h2 IDs
- **Related posts** in sidebar — Link to other posts
- **Prev/Next navigation** at the bottom

### 3.3 Add the Post to the Blog Listing Page
Open `blog/index.html` and add a new `<article>` block inside the `<div class="blog-grid">`:

```html
<!-- POST — copy and paste this block, fill in your details -->
<article class="blog-card reveal" data-cat="Tutorial">
  <span class="cat-badge">Tutorial</span>
  <h3>Your New Blog Post Title</h3>
  <p class="excerpt">A 1–2 sentence teaser of what the post covers.</p>
  <a href="posts/my-new-blog-post.html" class="read-more">Read More →</a>
  <div class="blog-meta"><span>May 06, 2026</span><span>5 min read</span></div>
</article>
```

**Categories available** (set `data-cat` to match the filter buttons):
- `Semiconductor`
- `EDA Tools`
- `Manufacturing`
- `Tutorial`

To add a new category, add a new filter button in `blog/index.html`:
```html
<button class="filter-btn" data-filter="New Category">New Category</button>
```

### 3.4 Update the Homepage (Optional)
To show your new post on the homepage, edit the blog section in `index.html` and update one of the three `<article class="blog-card">` blocks to point to your new post.

### 3.5 Commit and Push
```bash
git add .
git commit -m "Added new blog post: Your Post Title"
git push
```
Your post will be live in about 60 seconds.

---

## 🎨 Step 4: Customise the Design

All design tokens (colors, fonts, spacing) are in CSS variables at the top of each file's `<style>` block, and in `assets/shared.css`:

```css
:root {
  --accent: #00E5CC;    /* ← Change this to change the teal accent color */
  --bg: #0A0F1E;        /* ← Dark background */
  --heading: #ffffff;   /* ← Heading color */
}
```

**Common edits:**
| What to change | Where |
|---|---|
| Company name | `<title>` and `.logo` in each file |
| Contact info (email, phone, location) | `index.html` → `#contact` section |
| Social media links | `index.html` → `.socials` div |
| Accent color | `--accent` CSS variable |
| Navigation links | `<nav class="nav-links">` in each file |
| Footer columns | `<div class="footer-grid">` in each file |
| Stats numbers | `index.html` → `#stats` section, `data-count` attribute |

---

## 🔧 Tips & Tricks

- **Custom domain:** Go to Settings → Pages → Custom domain and enter your domain (e.g., `chipkraft.com`)
- **Google Analytics:** Add your GA4 script tag just before `</head>` in each HTML file
- **Contact form:** The current form shows a success message but doesn't send emails. To make it actually send emails, connect it to [Formspree](https://formspree.io) (free tier available) — just change the `<form>` tag to `<form action="https://formspree.io/f/YOUR_ID" method="POST">`
- **Images:** Put images in an `assets/images/` folder and reference them as `../../assets/images/your-image.jpg` from blog posts
- **Favicon:** Add a `favicon.ico` to the root folder and add `<link rel="icon" href="favicon.ico">` to each `<head>`

---

## ❓ Troubleshooting

| Problem | Solution |
|---|---|
| Site not updating after push | Wait 1–2 minutes; hard-refresh browser (Ctrl+Shift+R) |
| Blog post links don't work | Check the `href` path — it must match the filename exactly |
| CSS not loading on blog pages | Make sure `../../assets/shared.css` path is correct (two `../` from posts/) |
| Mobile menu not working | JavaScript must be at the bottom of `<body>`, not in `<head>` |
| Page shows 404 | Check Settings → Pages is enabled and pointing to the `main` branch |
