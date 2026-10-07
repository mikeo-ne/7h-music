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
  `artist-mike-1ne.jpg` is Mike 1ne's official Apple Music artist image, cropped to portrait.
- **Cover art:** `images/cover-*.jpg`.
- Roster & social handles: Spotify, Apple Music, Instagram, TikTok and YouTube links live inline next to each artist.
- **Mike 1ne (in-house producer & engineer):** roster row 03, three cards in *Fresh Out* (EP *Love Look What You Made Me Do*,
  single *Dance Di Night Away*, and his feature on Tungi's *Siteesa* — marked "Feature" and linked at track level), a Spotify
  player in *Now Playing*, and a footer column. He is **not** counted in the "Signed Artists" stat (still 2).
  Spotify artist `4DA5LBW4NWzVLcVSOrBLsI` · Apple Music artist `1840503931` · Instagram `@mike.1ne_` · TikTok `@mike.1ne_`.
  The footer's YouTube link is his auto-generated *Topic* channel — replace it with his own channel URL if he starts one.

## Contacts

- **General / Demos / Press & Booking:** 7hmusicgroupug@gmail.com
- **Producer / Studio (Mike 1ne):** mikeonerecords@gmail.com

## Contact form + demo uploads → FormSubmit

The contact form (with **demo file upload**) uses [FormSubmit](https://formsubmit.co) — free,
no signup, attachments arrive by email. Every topic goes to one inbox, set by `FORM_EMAIL` in
`index.html` (currently **7hmusicgroupug@gmail.com**).

**One-time activation (required):** the first submission to an address triggers a FormSubmit
email with an **"Activate Form"** button. Click it once in that inbox (check Spam/Promotions) —
after that every submission, including the attached demo, is delivered. If you ever change
`FORM_EMAIL` (and the `action` on the `<form>`), the new inbox needs activating the same way.

- Attachments: the file field is named `attachment` (FormSubmit's convention). Limit is 10 MB per
  submission; the form blocks files over 9 MB and tells the sender to share a Drive / SoundCloud link.
- FormSubmit replies HTTP 200 even when it refuses a message (e.g. inbox not activated), so the
  script reads `success` from the JSON body. On any failure the visitor sees a clickable email fallback.
- Spam: `_honey` honeypot field; the sender's email is set as Reply-To, subject includes the topic.
- Without JavaScript the form still posts natively to FormSubmit (their captcha page appears).
