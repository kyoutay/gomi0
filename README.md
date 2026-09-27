# gomi0.net

A barebones, zero-maintenance personal blog hosted on GitHub Pages.

## Directory Structure

```text
blog/
├── _config.yml               # Site metadata and global settings
├── _layouts/
│   ├── default.html          # Shell layout (HTML headers, footer)
│   └── post.html             # Individual blog post layout
├── _posts/
│   └── 2026-09-27-welcome-to-gomi0.md  # Blog entries (Markdown)
├── assets/
│   └── css/
│       └── style.css         # Barebones minimal CSS
├── index.html                # Homepage listing all posts
├── CNAME                     # Custom domain pointer (gomi0.net)
└── .gitignore
```

---

## 1. Initial Setup: Push to GitHub

1. Initialize git and commit:
   ```bash
   git init
   git add .
   git commit -m "Initial barebones blog setup"
   ```

2. Create a new repository on GitHub (public or private):
   - If public: GitHub Pages is free on any repo name.
   - Or name it `yourusername.github.io` or `blog`.

3. Push your repository:
   ```bash
   git branch -M main
   git remote add origin https://github.com/<YOUR-USERNAME>/<YOUR-REPO-NAME>.git
   git push -u origin main
   ```

4. Enable GitHub Pages in your repo:
   - On GitHub: **Settings** -> **Pages**.
   - Under **Build and deployment** -> **Source**: select **Deploy from a branch**.
   - Under **Branch**: select `main` and `/ (root)`, then click **Save**.

---

## 2. Transitioning `gomi0.net` from WordPress to GitHub Pages

Since `gomi0.net` is currently pointing to your WordPress host, you will switch it when you are ready for the new blog to take over:

1. **Log in to your domain registrar** (where `gomi0.net` was purchased, e.g. Namecheap, Cloudflare, GoDaddy, Porkbun, Google Domains/Squarespace, etc.).
2. Go to **DNS Management** for `gomi0.net`.
3. Update/replace the existing WordPress DNS records:
   - **Apex / Root Domain (`@` or `gomi0.net`)**:
     Add/update 4 `A` records pointing to GitHub Pages:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - **`www` Subdomain (`www.gomi0.net`)**:
     Add a `CNAME` record:
     - Host: `www`
     - Value: `<YOUR-GITHUB-USERNAME>.github.io`
4. In GitHub repository **Settings** -> **Pages**:
   - Verify `gomi0.net` appears in **Custom domain**.
   - Check **Enforce HTTPS** (GitHub will automatically provision a free SSL certificate once DNS finishes propagating, usually 5–30 minutes).

---

## 3. How to Write and Publish a Post

Whenever you want to post something new:

1. Create a new file in `_posts/` with the date and title:
   ```text
   _posts/YYYY-MM-DD-your-post-slug.md
   ```
2. Put the title at the top:
   ```markdown
   ---
   title: "Your Post Title"
   date: 2026-09-27
   ---

   Write your blog post in standard Markdown.
   ```
3. Commit and push:
   ```bash
   git add .
   git commit -m "New post: Your Post Title"
   git push
   ```

GitHub Pages will automatically build and publish it within seconds.
