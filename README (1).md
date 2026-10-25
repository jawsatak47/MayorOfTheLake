# Mayor of the Lake: Campaign Website

A fictional, satirical campaign site for the QuarkForce character **Mayor of the Lake**. One self-contained `index.html` (inline CSS and vanilla JS, no frameworks, no external requests except an optional YouTube player loaded on click).

## Folder structure

```
mayor-of-the-lake/
├── index.html
├── README.md
└── assets/
    └── mayor-of-the-lake.jpg   <-- your character poster (included)
```

The character poster is already included at `assets/mayor-of-the-lake.jpg`. To swap it, replace that file (same name), or change `CONFIG.posterPath` and the `<img>` and `og:image` references in `index.html`. If the file is ever missing, the hero shows a labeled placeholder instead of a broken image.

## Open locally

Double-click `index.html`, or for a more accurate test run a tiny server in the folder:

```
python3 -m http.server 8000
# then visit http://localhost:8000
```

## Deploy to GitHub Pages

1. Create a GitHub repository and upload `index.html`, `README.md`, and the `assets/` folder (with your image).
2. Repo **Settings → Pages → Build and deployment**: Source = *Deploy from a branch*, Branch = `main`, folder = `/ (root)`.
3. Wait a minute; your site appears at `https://YOUR-USERNAME.github.io/YOUR-REPO/`.
4. Set `CONFIG.siteUrl` to that URL, uncomment the `<link rel="canonical">` tag, and change `og:image` to the absolute image URL (social crawlers require absolute URLs).

## Configuration guide

Everything lives in the `CONFIG` block at the top of the `<script>`, plus the data arrays directly beneath it (`SLOGANS`, `QUOTES`, `PLATFORM`, `PROMISES`, `DEPTHS`, `NEWS`, `EVENTS`, `MERCH`, `FAQ`).

| Setting | What to do |
|---|---|
| `creatorName` | Your name/brand for IP attribution and the footer. |
| `siteUrl` | Your real public URL. Powers Copy Link and share buttons. |
| `email`, `mediaEmail`, `collabEmail`, `merchEmail` | Real addresses only. Empty ones are hidden. |
| `formEndpoint` | Form service URL (e.g. Formspree `https://formspree.io/f/XXXX`). Empty = honest "nothing was sent" dev mode. |
| `merchUrl` | Your existing shop. Per-product links go in `MERCH[].url`. |
| `donateUrl` | Leave empty unless you have a verified fundraising page and understand the rules. Empty shows a merch/participation CTA instead. |
| `pressKitUrl` | Path to a real ZIP (e.g. `assets/press-kit.zip`). Empty = placeholder dialog. |
| `universe`, `social` | QuarkForce, QuarkZine, JawsAtakTV, and social profile URLs. Empty ones are hidden. |
| `videos` | Add `{ title, url, kind }` with YouTube URLs. First is featured. |
| `EVENTS[]` | Add `start` as ISO with offset (`"2026-11-14T18:00:00-08:00"`), optional `end`, `tz` (`"America/Los_Angeles"`), and `rsvpUrl`. Events with a valid `start` show their date in that time zone and get **Add to Calendar** (.ics). Events without one show "Date to be announced". |
| `termsUrl`, `extraPolicyUrl`, `privacyExtra` | Footer links and a sentence naming your form processor. |

## Integrations needing separate accounts

- **Form processing:** Formspree, Netlify Forms, Basin, or similar. Spam protection: the form includes a hidden honeypot field; for stronger protection enable the service's reCAPTCHA/hCaptcha/Turnstile option in its dashboard (do not paste secret keys into this file).
- **Merch:** your existing shop (Square, Shopify, Printful, etc.).
- **Video:** YouTube (loaded privacy-enhanced, only on click).
- **Donations (optional):** a verified payment/fundraising service. Real electoral fundraising has legal requirements; this site is built as entertainment and does not provide any.

## Honesty rules built in

- Sample events and news are labeled fictional; no invented dates are shown as real.
- Forms never claim success unless the configured service returns an OK response.
- No payment or contact channel appears unless configured.
- No data is stored in the browser.

If this were ever adapted into a genuine electoral campaign, verify before publishing: candidate/committee registration, required "paid for by" sponsorship statements, campaign-finance disclosures, accessibility and privacy obligations, and election dates. None of that is provided here.

## Manual test checklist (not browser-tested)

1. Poster loads (or placeholder shows if the file is missing).
2. Every nav link scrolls to its section; mobile menu opens, closes on link click and Escape.
3. Platform cards expand; depth levels switch; FAQ opens/closes with keyboard (Tab, Enter/Space).
4. News and event filters change results; quote rotator Previous/Next/Pause/Copy work.
5. Submit both forms empty (errors appear), with a bad email (error), and valid (dev-mode message, no false success).
6. Copy Link works on the deployed site; share buttons appear only once a public URL exists.
7. With the OS "reduce motion" setting on, animations stop.
8. Resize to ~360px wide: no horizontal scrolling.
