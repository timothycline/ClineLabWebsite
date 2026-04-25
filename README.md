# Cline Lab Website

Fisheries Ecology at Montana State University — built with [Hugo](https://gohugo.io/) + [Blowfish](https://blowfish.page/) theme, deployed to GitHub Pages.

---

## Running the site locally

```bash
# Install Hugo and Go once (macOS):
brew install hugo go

# Start the development server (shows draft content too):
hugo server -D

# Open http://localhost:1313 in your browser.
# The page auto-reloads when you save a file.
```

---

## How to add content

### Add a new person

1. Create `content/people/firstname-lastname.md`
2. Use this front matter template:

```yaml
---
title: "First Last"
date: 2025-01-01          # date joined
role: "PhD Student"        # PI | Postdoc | PhD Student | MS Student | Undergraduate | Lab Manager
status: "current"          # current | alumni
year_started: 2025
# year_ended: 2027         # uncomment when they leave
photo: "img/people/firstname-lastname.jpg"   # place photo in assets/img/people/
email: "first.last@montana.edu"
links:
  scholar: "https://scholar.google.com/..."
  github: "https://github.com/..."
  website: "https://..."
weight: 10                 # lower = appears first (PI = 1)
---

Bio text goes here in normal markdown.
```

**To move someone to alumni:** just change `status: current` → `status: alumni` and add `year_ended`.
The site will automatically sort them into the Alumni section — no other changes needed.

---

### Add a publication

Create `content/publications/lastname-year-keyword.md`:

```yaml
---
title: "Full paper title"
date: 2025-06-01
authors: ["Timothy Cline", "Jane Doe", "Other Author"]
journal: "Journal Name"
volume: 12
issue: 3
pages: "100–115"
year: 2025
doi: "10.1234/journal.placeholder"
pdf: ""          # optional direct PDF link
tags: ["keyword1", "keyword2"]
featured: false  # set true to highlight on homepage
---

Optional abstract or notes here.
```

---

### Add a news post

Create `content/news/YYYY-MM-short-title.md`:

```yaml
---
title: "Paper published in Journal X"
date: 2025-04-15
tags: ["publication", "award", "field work"]
---

Write the news item in normal markdown below the front matter.
```

---

### Add a project or dataset

Create `content/projects/short-name.md`:

```yaml
---
title: "Tool or Dataset Name"
date: 2025-01-01
description: "One-sentence description shown in cards."
image: "img/projects/short-name.png"
links:
  github: "https://github.com/..."
  demo: "https://..."
  data: "https://doi.org/..."
  paper: "/publications/lastname-year-keyword/"
tags: ["tools", "data", "R"]
featured: false   # set true to show on homepage
---

Longer description, what's included, how to use it, etc.
```

---

## Updating site configuration

All site settings live in `config/_default/`:

| File | What it controls |
|---|---|
| `hugo.toml` | Base URL, site title, Hugo module imports |
| `languages.en.toml` | Site description, author name |
| `menus.en.toml` | Navigation bar links |
| `params.toml` | Color scheme, header/footer, author info, social links |

**To change the color scheme:** edit `colorScheme` in `params.toml`.
Options: `ocean`, `avocado`, `fire`, `forest`, `princess`, `slate`, `terminal`, `tide`, `tokyonight`.

---

## Deployment (GitHub Pages)

### One-time setup

1. Create a new repository on GitHub (e.g., `clinelab/website`)
2. In the repo → **Settings → Pages → Source**: select **GitHub Actions**
3. Push this folder:

```bash
git remote add origin git@github.com:timothycline/ClineLabWebsite.git
git push -u origin main
```

4. Update `baseURL` in `config/_default/hugo.toml` to match your GitHub Pages URL:
   ```
   https://YOUR-USERNAME.github.io/YOUR-REPO/
   ```

After that, every push to `main` automatically rebuilds and redeploys the site.

### Custom domain (optional)

If you have a custom domain (e.g., `clinelab.montana.edu`):
1. Add a `CNAME` file to the `static/` folder containing your domain name
2. Update `baseURL` in `hugo.toml` to `https://clinelab.montana.edu/`
3. Configure the DNS record with your domain registrar/IT

---

## Adding photos

Place photos in `assets/img/people/` and reference them as `img/people/firstname-lastname.jpg` in front matter.
Hugo will resize and optimize them automatically.

For project images: `assets/img/projects/short-name.png`.

---

## Theme documentation

Full Blowfish docs: https://blowfish.page/docs/
