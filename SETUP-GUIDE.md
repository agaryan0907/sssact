# SSSACT Website — Setup Guide

This folder contains your finished website:

- **index.html** — the entire website (one file, all design + code built in)
- **logo.jpeg** — the SSSACT logo used on the site

The QR donation code, fonts, and layout all work as-is. You only need to do
**two things** to make it fully live: (1) host it on GitHub Pages, and
(2) connect Google Analytics. Both are 100% free. Steps below.

---

## PART 1 — Put the site online with GitHub Pages (free)

1. Create a free account at https://github.com (skip if you have one).
2. Click the **+** (top-right) → **New repository**.
   - Repository name: `sssact` (or anything you like)
   - Set it to **Public**
   - Click **Create repository**.
3. On the new repo page, click **uploading an existing file** (a link in the
   middle of the page).
4. Drag **both** `index.html` and `logo.jpeg` into the upload box.
5. Click **Commit changes**.
6. Go to the repo's **Settings** tab → **Pages** (left sidebar).
7. Under "Build and deployment" → **Source**, choose **Deploy from a branch**.
   - Branch: **main**, folder: **/ (root)** → click **Save**.
8. Wait ~1 minute, refresh the page. GitHub shows a green link like:
   `https://YOUR-USERNAME.github.io/sssact/`
   **That is your live website.** 🎉

---

## PART 2 — Connect Google Analytics 4 (free, gives you the data for your assignment)

Google Analytics 4 (GA4) is completely free — there is no paid version you need
to buy. You just create a property and paste one ID into the file.

1. Go to https://analytics.google.com and sign in with any Google account.
2. Click **Start measuring** (or Admin ⚙️ → **Create** → **Account**).
   - Account name: `SSSACT`
   - Property name: `SSSACT Website`
   - Pick your time zone (India) and currency (INR).
3. Under "Platform", choose **Web**.
   - Website URL: paste your GitHub Pages link from Part 1.
   - Stream name: `SSSACT`
   - Click **Create stream**.
4. You'll see a **Measurement ID** that looks like `G-XXXXXXXXXX`. Copy it.
5. Open `index.html` in any text editor (Notepad works). Near the very top,
   find these lines (there are **two** places with `G-XXXXXXXXXX`):

   ```
   <script async src="https://www.googletagmanager.com/gtag/js?id=G-XXXXXXXXXX"></script>
   ...
   gtag('config', 'G-XXXXXXXXXX');
   ```

6. Replace **both** `G-XXXXXXXXXX` with your real Measurement ID. Save the file.
7. Re-upload the edited `index.html` to GitHub (repo → `index.html` → pencil
   icon → paste → Commit), OR just drag-and-drop to overwrite.
8. Open your live site once in your browser. Within a minute, GA4 →
   **Reports** → **Realtime** will show **1 active user** (that's you). Done!

After a day or two you'll have real data: visitor counts, locations, devices,
which sections people view — perfect for your assignment results.

---

## The on-page visitor counter

The footer shows a live "Visitors" number using a free service called CountAPI
(no signup needed). It works automatically once the site is online.

- It uses the namespace `sssact-bengaluru/visits`. If you want your own fresh
  count, open `index.html`, find `sssact-bengaluru` (near the bottom in the
  script), and change it to any unique word, e.g. `sssact-myname-2026`.

> Note: this counter only works on the **live (https) site**, not when you open
> the file directly from your computer. That's normal.

---

## Connecting the forms (Volunteer + Review) — free, 5 minutes

The Volunteer and Review forms are ready, but they need one free service to
deliver submissions to your inbox. Until you connect it, clicking "submit" shows
a friendly "not connected yet" message (it won't break).

We use **Formspree** (free tier: 50 submissions/month — plenty for an NGO).

1. Go to https://formspree.io and sign up (free) using **sssactb@gmail.com**
   so submissions arrive at the trust's email.
2. Click **+ New Form**. Name it `SSSACT Volunteer`. For the email it sends to,
   use **sssactb@gmail.com**. Click create.
3. Formspree gives you an endpoint URL like:
   `https://formspree.io/f/abcdwxyz` — copy the part after `/f/` (e.g. `abcdwxyz`).
4. Open `index.html`, search for **`YOUR_FORM_ID`** (it appears **twice** — once
   for the volunteer form, once for the review form).
5. Replace each `YOUR_FORM_ID` with your form ID. If you want volunteer and
   review submissions separated, create **two** Formspree forms and use a
   different ID in each spot. (Using the same ID for both is fine too.)
6. Save and re-upload `index.html` to GitHub.
7. Test: open your live site, submit the volunteer form once. The first time,
   Formspree emails you to confirm the address — click the link. After that, all
   submissions land in the inbox automatically.

> Why a service is needed: GitHub Pages only serves files; it can't receive form
> data or send email on its own. Formspree handles that part for free.

---

## Adding & editing Events Conducted

The events section shows four past events, each with a photo and description.
To add another event:

1. Open `index.html` and find the `<!-- ===== EVENTS CONDUCTED ===== -->` section.
2. Copy one full `<article class="event-card">…</article>` block.
3. Paste it inside `<div class="events-list">` and edit the photo (`src`), the
   **tag**, **title**, **description** and **location**.
4. To keep the alternating left/right layout, add the word `reverse` to the
   class on every second card: `<article class="event-card reveal reverse">`.
5. Put any new photo in the `images/` folder and point `src` to it, e.g.
   `images/my-new-photo.jpg`.

## Adding photos to the Gallery

1. Drop your new image file into the `images/` folder.
2. In `index.html`, find `<!-- ===== GALLERY ===== -->` and copy one
   `<button class="gal-item" …>…</button>` line.
3. Paste it into `<div class="gal-grid">` and update **both** the `data-src` and
   the `<img src>` to your new filename, plus a short `alt` description.
4. Save and re-upload. The click-to-enlarge lightbox works automatically.

## Adding reviews to the page

Reviews submitted through the form arrive by email. To publish a good one on the
site, find the `<!-- ===== REVIEWS ===== -->` section, copy a `<div class="rev">…
</div>` card, and edit the stars (★), review text, and the person's name/role.

---

## ⚠️ IMPORTANT: uploading the photos to GitHub

Your site now uses a folder called **`images/`** that holds all the event and
gallery photos. When you upload to GitHub, you must upload this **whole folder**,
not just `index.html` — otherwise the photos will show as broken.

Easiest way to upload everything at once:

1. On your repo's main page, click **Add file → Upload files**.
2. **Drag the entire `sssact-website` folder contents** — `index.html`,
   `logo.jpeg`, **and** the `images` folder — into the upload area at the same
   time. GitHub keeps the folder structure.
3. Scroll down → **Commit changes**.
4. Wait ~1 minute, then open your live site. The Events and Gallery photos
   should all appear.

> If you ever see broken image icons, it almost always means the `images/`
> folder (or a specific file inside it) didn't get uploaded. Re-upload the
> folder and they'll appear.

---

## Editing the content later

Everything is plain text inside `index.html`. To change wording, search for the
text you see on the site and edit it. Some useful spots:

- **Phone number:** search for `tel:+910000000000` and put the real number.
- **UPI / QR:** the QR encodes `32683881028@SBI`. If the UPI ID ever changes,
  regenerate the QR (or ask me to) and update the UPI ID text.
- **Address / email:** search for `Nagasandra` or `sssactb@gmail.com`.

---

## Quick checklist

- [ ] Upload `index.html` + `logo.jpeg` to GitHub
- [ ] Turn on GitHub Pages → get your live link
- [ ] Create GA4 property → copy `G-XXXXXXXXXX`
- [ ] Paste the ID into `index.html` (2 places) → re-upload
- [ ] Visit the live site → confirm GA4 Realtime shows you
- [ ] Sign up at Formspree → paste your form ID over `YOUR_FORM_ID` (2 places)
- [ ] Test the volunteer form → confirm the email arrives
- [ ] Add your first real event (and remove the placeholder)
- [ ] (Optional) Personalise the visitor-counter namespace

That's it — a clean, professional, fully-tracked NGO website at zero cost.
