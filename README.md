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
  `artist-mike-1ne.jpg` is the photo Mike 1ne supplied, cropped to a 4:5 portrait (the Instagram mute icon is cropped out).
  `artist-smokie-cee.jpg` is currently the *Island Kiss* single artwork (his official profile image on Spotify, Apple Music and TikTok),
  cropped 4:5 — replace it with a real portrait (same filename, 4:5, at least 640×800) once he supplies one.
- **Cover art:** `images/cover-*.jpg`.
- Roster & social handles: Spotify, Apple Music, Instagram, TikTok and YouTube links live inline next to each artist.
- **Mike 1ne (in-house producer & engineer):** roster row 03, three cards in *Fresh Out* (EP *Love Look What You Made Me Do*,
  single *Dance Di Night Away*, and his feature on Tungi's *Siteesa* — marked "Feature" and linked at track level), a Spotify
  player in *Now Playing*, and a footer column. He is **not** counted in the "Signed Artists" stat (that counts Baranga,
  Mr Fallback and Smokie Cee = 3); he has his own "In-House Producer" stat instead.
  Spotify artist `4DA5LBW4NWzVLcVSOrBLsI` · Apple Music artist `1840503931` · Instagram `@mike.1ne_` · TikTok `@mike.1ne_`.
  The footer's YouTube link is his auto-generated *Topic* channel — replace it with his own channel URL if he starts one.
- **Smokie Cee:** roster row 04, two cards in *Fresh Out* (his single *Island Kiss* ft. Baranga, and Baranga's single *Confirm*,
  which is co-billed to him), a Spotify player for *Island Kiss* in *Now Playing*, a footer column and a ticker line.
  Counted in "Signed Artists". Spotify artist `1sdWhxn7YxWfsDIEUCwRwt` · Apple Music artist `1798636079` ·
  TikTok `@smokie_ceee` · YouTube `@smokie_cee`. No Instagram link yet — none could be verified.
  Spotify also has an empty duplicate profile (`4w8cimov72F0F1kefN5klH`) credited on *Confirm*; his distributor can merge the two.
- **Now Playing players** are 352 px tall (Spotify's standard large embed) so every card lines up. The grid is 2 × 2; add an artist
  by copying a `.listen-card` (an odd count automatically stretches the last card across the row).

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
