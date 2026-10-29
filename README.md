# cioffiscientific.com

Personal site for Alexander G. Cioffi, Ph.D. Plain HTML + CSS — no frameworks, no build step.
GitHub Pages serves these files exactly as they are.

## Files

| File | What it is |
|---|---|
| `index.html` | Home page: photo, intro, expertise, career timeline, contact |
| `publications.html` | Papers (newest first) and patent applications |
| `projects.html` | Showcase cards for the proteomics notebooks |
| `styles.css` | One stylesheet shared by every page — colors/fonts live at the top |
| `images/headshot.jpg` | Home page photo. Square-ish, ≥ 600×600 px, < 500 KB |
| `images/social-preview.png` | 1280×640 card shown when a page is shared (LinkedIn, Slack, texts) |
| `CNAME` | One line telling GitHub Pages which domain this site answers to |

## Preview locally

Open `index.html` in a browser by double-clicking it. For a closer match to the live site:

```bash
cd cioffiscientific
python -m http.server 8000
# then visit http://localhost:8000
```

## Publish on GitHub Pages (one time)

1. On GitHub, create a **public** repository, e.g. `cioffiscientific.com`.
2. Upload these files to the repository root (the CNAME file must be at the root).
3. Repo **Settings → Pages**: Source = *Deploy from a branch*, Branch = `main`, folder = `/ (root)`. Save.
4. Same page, **Custom domain**: enter `cioffiscientific.com`, Save.
   (Do this *before* the DNS step — GitHub's docs warn that pointing DNS first can let someone else claim the domain.)

## Point the Namecheap domain at GitHub (one time)

Namecheap → Domain List → `cioffiscientific.com` → **Manage → Advanced DNS**.
Delete the default parking records (the `CNAME www → parkingpage.namecheap.com` and the URL-redirect record), then add:

| Type | Host | Value |
|---|---|---|
| A Record | `@` | `185.199.108.153` |
| A Record | `@` | `185.199.109.153` |
| A Record | `@` | `185.199.110.153` |
| A Record | `@` | `185.199.111.153` |
| CNAME Record | `www` | `acioffi3-spec.github.io.` |

DNS can take up to 24 h to propagate. Then back in **Settings → Pages**, tick **Enforce HTTPS**
(it may be greyed out until the certificate is issued).

Check DNS from a terminal: `dig cioffiscientific.com +noall +answer` (macOS/Linux) or
`Resolve-DnsName cioffiscientific.com` (Windows PowerShell).

## Routine edits

- **New paper:** copy a `<li class="pub">…</li>` block in `publications.html`, paste at the top, edit.
- **Notebook goes live:** in `projects.html`, change `In progress` to `Live`, add `live` to the
  status class, and uncomment/replace the notebook link.
- **Portfolio repo goes public:** in `projects.html`, un-comment the hidden "View the repository" button and set its URL.
- **Change colors:** edit `--accent` and `--accent-2` at the top of `styles.css`.
- **Wording:** the site uses "mass spectrometry-driven" throughout; keep new copy consistent.

Commit and push; GitHub Pages republishes within a minute or two.
