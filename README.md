# SigmaEta × Grant Thornton Bharat — Certification Microsite

A single-page, mobile-and-laptop responsive site for the GT Bharat certification drive,
built for SigmaEta, The Operations Club of IIM Trichy.

---

## 1. Before you share it — two links to fill in

Open `index.html`, scroll to the bottom, and find the `CONFIG` block inside `<script>`:

```js
const CONFIG = {
  REGISTRATION_URL : "PASTE_REGISTRATION_FORM_LINK_HERE",
  WHATSAPP_URL     : "PASTE_OPSHOUSE_WHATSAPP_INVITE_HERE"
};
```

Replace both strings and save. Every "Register" button on the page (10 of them) and the
WhatsApp button read from these two values, so you only edit them once.

---

## 2. File structure

```
sigmaeta-gt-certifications/
├── index.html                                          the whole site (HTML + CSS + JS)
├── README.md                                           this file
├── assets/
│   ├── sigmaeta-logo.png                               full club lockup, transparent PNG
│   ├── sigmaeta-mark.png                               flame mark only, for small sizes
│   ├── favicon.png                                     64×64 browser tab icon
│   ├── apple-touch-icon.png                            180×180 iOS home-screen icon
│   └── og-share-image.png                              1200×630 link-preview image
└── pdfs/
    ├── gt-lean-six-sigma-programme.pdf                 Green Belt + Black Belt + FastTrack
    ├── gt-business-consulting-and-strategy.pdf
    └── gt-advanced-data-insights-and-visualization.pdf
```

Naming rules used throughout: lowercase, hyphen-separated, no spaces, no capitals.
This matters — many web hosts are case-sensitive, and a file named `Logo.PNG`
will 404 when the HTML asks for `logo.png`.

**Keep the three folders together.** All links are relative, so the site works as long as
`index.html`, `assets/` and `pdfs/` sit side by side. Moving one breaks the links.

---

## 3. Publishing

Any static host works. Two easy options:

**Netlify Drop** — go to app.netlify.com/drop and drag the whole
`sigmaeta-gt-certifications` folder onto the page. You get a live URL in about ten seconds.
Rename the site in Site settings to get something like `sigmaeta-gt.netlify.app`.

**GitHub Pages** — create a repository, upload the folder contents to the root of the
`main` branch, then Settings → Pages → Source: `main` / `root`.

Once live, the link preview image will appear automatically when the URL is shared on
WhatsApp or LinkedIn. For that to work, change the `og:image` tag in `index.html` from the
relative path to the full URL, e.g.
`<meta property="og:image" content="https://your-site-url/assets/og-share-image.png">`.

To test locally before publishing, open a terminal in this folder and run
`python3 -m http.server 8000`, then visit `http://localhost:8000`.

---

## 4. Things you may want to change later

| What | Where in `index.html` |
|---|---|
| Registration and WhatsApp links | `CONFIG` block at the bottom |
| Fees | Each programme's `.ladder` block, plus the summary `<table>` — update both |
| Programme names and prices in the tabs | The five `<button class="tab">` elements |
| Syllabus content | Inside each `<details>` block |
| Colours | The `:root` variables at the top of the `<style>` block |

If you need a deadline line back on the page, add it under the hero buttons — the countdown
that was there earlier has been removed.

---

## 5. A note on the PDFs

The three course decks carry Grant Thornton's confidentiality notice. Before putting them on
a public URL, it's worth a quick confirmation from your GT contact. If they'd rather the decks
weren't publicly indexed, host them on Drive with access restricted to `iimtrichy.ac.in` and
swap the four `href="pdfs/..."` values in `index.html` for those Drive links.

---

Programme content and course PDFs © 2026 Grant Thornton Bharat LLP.
Site assembled for SigmaEta, The Operations Club of IIM Trichy.
