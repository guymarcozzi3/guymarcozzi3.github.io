# Site Editor's Guide
### How to update your website — no technical experience required

---

## Where Each Page Lives

| Page | File to Edit |
|---|---|
| Home | `index.md` |
| Bio | `bio.md` |
| Book | `book.md` |
| Speaking | `speaking.md` |
| Podcast | `podcast.md` |
| Site name, email, LinkedIn | `_config.yml` |

Open any `.md` file in a plain text editor (Notepad, TextEdit, VS Code, etc.) to edit it.

---

## 1. How to Edit Text (Markdown Basics)

Markdown is plain text with a few simple symbols for formatting.

| What you want | What you type |
|---|---|
| **Bold** | `**bold text**` |
| *Italic* | `*italic text*` |
| Heading | `## Section Title` |
| Sub-heading | `### Sub-heading` |
| Bullet list | `- Item one` |
| Horizontal rule | `---` |
| Link | `[Link text](https://url.com)` |
| Pull quote | `> "Quote text here."` |
| Line break | Leave a blank line between paragraphs |

**Example:**

```
## About

I've spent 25 years advising CEOs and boards through complex change.

My work focuses on three things: **strategy**, **culture**, and **execution**.
```

---

## 2. How to Add or Replace Images

### Headshot (Home page)
1. Name your photo file `headshot.jpg`
2. Put it in the `assets/images/` folder
3. Open `index.md` and find this block:

```html
<!-- Replace the placeholder below with your actual photo:
     <img src="/assets/images/headshot.jpg" alt="[Your Name]" /> -->
<div class="hero-photo-placeholder">Your Photo Here</div>
```

4. Delete the `<div class="hero-photo-placeholder">...</div>` line
5. Uncomment (remove the `<!--` and `-->`) the `<img>` line
6. Replace `[Your Name]` with your name

### Book Cover
1. Name your file `book-cover.jpg`
2. Put it in `assets/images/`
3. Open `book.md` and do the same swap — find the `book-cover-placeholder` div, replace it with the `<img>` tag above it (remove the comment markers)

**Image tips:**
- JPG or PNG both work
- Headshot: use a high-res file, ideally 800px wide or larger
- Book cover: publisher usually provides a high-res image

---

## 3. How to Add Videos (YouTube or Vimeo)

Open `speaking.md` and find the `<div class="video-item">` blocks.

### YouTube
1. Go to the YouTube video
2. Copy the URL — e.g. `https://www.youtube.com/watch?v=ABC123xyz`
3. The video ID is the part after `v=` → `ABC123xyz`
4. Your embed URL is: `https://www.youtube.com/embed/ABC123xyz`
5. Paste it into the `src="..."` of the iframe

### Vimeo
1. Go to the Vimeo video
2. Copy the URL — e.g. `https://vimeo.com/123456789`
3. The video ID is `123456789`
4. Your embed URL is: `https://player.vimeo.com/video/123456789`
5. Paste it into `src="..."`

### To add a third (or fourth) video:
Copy the entire `<div class="video-item">...</div>` block and paste it below the last one. Fill in the new title, description, and embed URL.

---

## 4. How to Publish Changes (GitHub)

Every time you save a file and push it to GitHub, the site updates automatically within ~60 seconds.

### Option A — GitHub Desktop (easiest, no command line)
1. Open GitHub Desktop
2. You'll see your changed files listed on the left
3. Add a short summary in the "Summary" box (e.g. "Update bio")
4. Click **Commit to main**
5. Click **Push origin**
6. Done — your site will update in about a minute

### Option B — Command Line
```bash
git add .
git commit -m "Update bio"
git push
```

### To verify your site updated:
Visit your domain. If it hasn't updated after 2 minutes, go to your GitHub repo → **Actions** tab to check for errors.

---

## 5. First-Time Setup Checklist

Before your site goes live, fill in these placeholders:

**In `_config.yml`:**
- [ ] Replace `[YOUR FULL NAME]` with your actual name
- [ ] Replace `https://yourdomain.com` with your domain
- [ ] Replace `yourhandle` in the LinkedIn URL
- [ ] Replace `you@yourdomain.com` with your email

**In `index.md`:**
- [ ] Replace all `[Your Name]` and `[Your Book Title]` references
- [ ] Swap in your headshot (see Section 2 above)

**In `bio.md`:**
- [ ] Replace all placeholder text with your actual bio and experience

**In `book.md`:**
- [ ] Fill in book title, subtitle, description, and purchase links
- [ ] Add your book cover image

**In `speaking.md`:**
- [ ] Fill in your talk topics and descriptions
- [ ] Replace placeholder YouTube embed URLs with real ones

**Connecting your domain (Namecheap → GitHub Pages):**
1. In your GitHub repo, go to **Settings → Pages**
2. Set Source to `Deploy from a branch`, branch: `main`, folder: `/ (root)`
3. Enter your custom domain in the "Custom domain" field and save
4. In Namecheap, go to your domain's DNS settings and add:
   - Four `A` records pointing to GitHub's IPs:
     - `185.199.108.153`
     - `185.199.109.153`
     - `185.199.110.153`
     - `185.199.111.153`
   - One `CNAME` record: `www` → `yourusername.github.io`
5. Wait up to 24 hours for DNS to propagate. GitHub will also provision an SSL certificate automatically.

---

*Questions? Open an issue in the GitHub repo or refer to [GitHub Pages documentation](https://docs.github.com/en/pages).*
