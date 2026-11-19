# DuosApp — official website

Static site for [DuosApp](https://play.google.com/store/apps/details?id=com.duosapp), hosted on GitHub Pages.
No build step, no framework: plain HTML + one stylesheet. Edit a file, commit, and GitHub Pages republishes within a minute or two.

**Live site:** https://www.myduos.app/ (custom domain, set by the `CNAME` file — don't delete it, or the site falls back to the GitHub Pages address and the app's policy links break)

## Pages

| File | URL | Purpose |
|---|---|---|
| `index.html` | `/` | Homepage |
| `terms.html` | `/terms.html` | Terms & Conditions |
| `privacy.html` | `/privacy.html` | Privacy Policy |
| `delete-account.html` | `/delete-account.html` | Data Deletion Policy (Play Console "account deletion" URL) |
| `community-guidelines.html` | `/community-guidelines.html` | Community Guidelines |
| `refund-policy.html` | `/refund-policy.html` | Refund & Cancellation Policy |
| `child-safety.html` | `/child-safety.html` | Child Safety Standards (Play Console CSAE URL) |
| `404.html` | — | Shown for broken links |

`privacy.html`, `terms.html` and `delete-account.html` keep their original filenames on purpose — if they are already entered in Play Console, nothing needs re-submitting.

## Editing

- **Text on any page:** open the `.html` file and edit the content between `<article class="policy-card">` … `</article>` (policies) or inside `<main>` (homepage). Keep the `<h2 id="…">` ids — the "On this page" list links to them.
- **Dates:** each policy has a `Last updated:` line near the top. Change it when you change the policy.
- **Colours, fonts, spacing:** `assets/css/site.css`. The brand tokens are in the `:root` block at the top; change them there and every page follows.
- **Font:** Poppins is self-hosted from `assets/fonts/` (SIL Open Font License, see `LICENSE-Poppins.txt` there) — no request goes to Google Fonts. To change the typeface, replace the `.woff2` files and the `@font-face` block at the top of `site.css`.
- **Support email / Play link:** search the repo for `duosapp.support@gmail.com` and `id=com.duosapp` and replace.
- **Screenshots:** `assets/img/screens/`. Each screen has a `name.webp` (470 px wide) and `name@2x.webp` (940 px) for sharp displays. To add one, drop in both sizes and copy a `<figure>` block in `index.html`.
- **Reel:** `assets/video/reel.mp4` (poster: `reel-poster.jpg`). Keep it under ~2 MB so the homepage stays fast.
- **Header and footer** are repeated in every file (no templating), so a change to them is a change to all seven pages.

## Google Play "Get it on Google Play" badge

The download buttons are styled in-house to avoid shipping Google's trademarked badge without its licence. If you'd rather use the official badge, download it from https://play.google.com/intl/en_us/badges/ (accept the terms), save it to `assets/img/`, and replace the `<a class="btn btn-primary btn-store" …>` elements with an `<img>` inside the link.

## Publishing on GitHub Pages

Settings → Pages → *Build and deployment* → Source: **Deploy from a branch** → Branch: **main**, folder **/ (root)** → Save.
The `.nojekyll` file tells Pages to serve files as-is.
