# 7H Music Group — Website

The official site for **7H Music Group** — a Kampala-based record label, management and publishing house.

A pure static site: plain **HTML + CSS + vanilla JS**. No build step, no frameworks, no dependencies.

## Structure

```
index.html      ← the whole site (home/landing)
404.html        ← branded 404 page (served automatically by Vercel)
favicon.svg     ← tab icon (vector)
favicon.png     ← tab icon (180px fallback / Apple touch icon)
images/         ← photos, artist press shots, release cover art
vercel.json     ← Vercel config (clean URLs)
```

## Run locally

Any static file server works, e.g.:

```bash
python3 -m http.server 8080
# open http://localhost:8080
```

## Deploy (GitHub → Vercel)

1. Push this folder to a GitHub repository.
2. Go to [vercel.com](https://vercel.com) → **Add New… → Project** → import the repo.
3. Framework preset: **Other** (no build command).
   - **Build command:** leave blank
   - **Output directory:** `.` (root)
4. Click **Deploy**. Every push to `main` auto-deploys.

Notes:
- `vercel.json` enables **clean URLs** and Vercel automatically serves **`404.html`** with a proper 404 status.
- The Spotify embeds and external links work in the deployed site (iframes are only blocked inside in-app/sandboxed previews, not a real browser).

## Editing

- **Roster / releases / links:** all content is in `index.html` — each artist, release and link is clearly marked.
- **Artist photos:** `images/artist-*.jpg` — replace a file with a real press photo of the same name (portrait orientation works best).
- **Cover art:** `images/cover-*.jpg`.
- Roster & social handles: Spotify, Apple Music, Instagram, TikTok and YouTube links live inline next to each artist.

## Contacts

- **General / Press & Booking:** 7hmusicgroup@gmail.com
- **Demos & A&R:** declanmike12@gmail.com
- **Producer / Studio (Mike 1ne):** mikeonerecords@gmail.com

## Contact form + demo uploads → FormSubmit

The contact form (with **demo file upload**) uses [FormSubmit](https://formsubmit.co) — free,
no signup, attachments arrive by email. Routing in `index.html` (`FORM_ROUTES`):

- **Artist / Demo** and **Producer / Songwriter** → declanmike12@gmail.com (A&R)
- **Brand partnership / Press / Other** → 7hmusicgroup@gmail.com (general)

**One-time activation (required):** the first submission to each address triggers a FormSubmit
email with an **"Activate Form"** button. Click it in **both** inboxes (declanmike12@ and
7hmusicgroup@) — after that every submission, including the attached demo, is delivered.
- Attachments: up to ~10 MB, sent straight to the inbox (MP3/WAV/M4A). Larger files should be
  shared via a Google Drive / SoundCloud link in the message (the form enforces this client-side).
- Spam is filtered with the `_honey` honeypot field; the user's email is set as Reply-To.
