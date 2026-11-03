# Class Blog

A tiny Jekyll blog for four people, hosted for free on GitHub Pages.
No build tools, no dependencies to update — GitHub builds it on every push.

```
_config.yml        site title, course name, baseurl   ← edit once
_data/authors.yml  the four people                   ← edit once
_posts/            one Markdown file per post         ← this is where you work
assets/img/        images for posts
assets/css/        the whole look (one file, colors at the top)
_layouts/          page templates (rarely touched)
```

---

## 1 · One-time setup (≈5 min, one person does it)

1. Create a new **public** repo on GitHub, e.g. `class-blog`.
2. Upload all these files (drag & drop on the repo page works, or `git push`).
3. Repo → **Settings → Pages** → *Build and deployment* → Source: **Deploy from a branch**, Branch: **main** / **(root)** → Save.
4. Open `_config.yml` and set:
   - `title`, `description`, `course`
   - `baseurl: "/class-blog"` — must match the repo name. (If the repo is named `<username>.github.io`, use `""`.)
5. Open `_data/authors.yml` and put in your four names/bios.
6. Repo → **Settings → Collaborators** → add the other three with *Write* access.

After ~1 minute the blog is live at
`https://<username>.github.io/class-blog/` — that's the link for the professors.

---

## 2 · Writing a post (everyone) — the visual editor

No Markdown needed. Uses [Pages CMS](https://pagescms.org), a free editor that works on top of this repo.

1. Go to **https://app.pagescms.org** and **Sign in with GitHub**.
2. The first time, it asks you to install the Pages CMS GitHub app. Allow it for this repo only.
   (Only the repo owner needs to do this. Collaborators just sign in.)
3. Pick the blog repo → **Posts → Add an entry**.
4. Title, author, date, text. Use the toolbar for formatting and drag images straight in.
5. **Save**. The post is live about a minute later.

Untick **Published** to save a draft. To edit or delete a post, open it from the list.

**Image size:** click an image in the editor → alt-text field → start it with a size word:

| alt text starts with | size |
|---|---|
| *(nothing)* | natural size, max. text width |
| `small:` | ⅓ of the text column. Up to 3 small images sit side by side, then wrap |
| `medium:` | ⅔ of the text column. Fits next to one small image |
| `large:` | full text column |
| `wide:` | wider than the text, to the right page edge |

e.g. `wide: robot arm collecting tears, sketch`

**Headings:** a heading applies to the whole paragraph. Press **Enter** to start a new
line *before* turning it into a heading. Lines pasted in or separated with Shift+Enter
count as one paragraph, so the whole block becomes a heading.
There's also a "Write a post ↗" link in the site footer.

**Adding/renaming people:** update `_data/authors.yml` *and* the `values:` list under
`author` in `.pages.yml` (both use the same short keys, e.g. `claudio`).

### Alternative: plain Markdown on GitHub
1. Open the `_posts` folder on GitHub → **Add file → Create new file**.
2. Name it `YYYY-MM-DD-short-title.md`, e.g. `2026-11-10-first-prototype.md`.
3. Paste and fill in:

   ```markdown
   ---
   title: "First prototype"
   author: claudio
   tags: [prototype, research]
   ---

   Your text in Markdown…
   ```
4. **Commit changes**. Live in about a minute.

`author:` must be one of the keys from `_data/authors.yml` (`claudio`, `person2`, …).

### Images
Upload to `assets/img/` (**Add file → Upload files**), then in the post:

```markdown
![What's in the image]({{ '/assets/img/my-photo.jpg' | relative_url }})
*Optional caption*
```
Keep images small (JPG/WebP, ~2000 px wide, < 1 MB).

### Video
Paste YouTube/Vimeo embed `<iframe>` code straight into the post.

### Drafts / future dates
A post with a date in the future won't show until that day.
To hide a post, add `published: false` to its header.

---

## 3 · Avoiding conflicts

Each person only creates/edits **their own** post files, so you'll almost never clash.
If you use git locally: `git pull` before you start, `git push` when you're done.

---

## 4 · Preview locally (optional)

```bash
bundle install
bundle exec jekyll serve
# → http://localhost:4000/class-blog/
```

## 5 · Changing the look

Everything visual is in `assets/css/style.css`. The colors and fonts are the
variables at the very top — change those and the whole site follows.
Dark mode is automatic.
