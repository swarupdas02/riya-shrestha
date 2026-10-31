# AGENTS.md: Project Reference for riya-shrestha

Context for any AI agent or developer working on this repository. Last updated 31 Oct 2026.

---

## 1. What this project is

A single page online CV for **Riya Shrestha** (banking compliance / AML-CFT professional, Kathmandu, Nepal). It is hosted on **GitHub Pages** with a custom domain bought on **Hostinger**.

| Item | Value |
| :--- | :--- |
| Repository | `riya-shrestha` (GitHub user `swarupdas02`) |
| Default Pages URL | `https://swarupdas02.github.io/riya-shrestha/` |
| Custom domain | `riyashrestha.id` (plus `www.riyashrestha.id`) |
| Registrar / DNS | Hostinger hPanel |
| Stack | Static HTML (`index.html`) + local stylesheet (`styles.css`). No build step, no framework, no JS dependencies, no CDN. |

### Goals (from the owner)
1. Turn a Markdown CV source into a polished, professional CV.
2. Make it work both as a **web page** and as a **one page A4 PDF** (print/export).
3. Host it for free on GitHub Pages under the custom domain.
4. Keep the writing in **British English**, with no em dashes and no unnecessary hyphens.

---

## 2. Repository structure

```text
riya-shrestha/
├── index.html           # Semantic CV markup + SEO / OpenGraph / JSON-LD metadata
├── styles.css           # All CSS: desktop base, dark mode, responsive (@media screen), and print (@media print)
├── CV.md                # Single Source of Truth (SSOT) for all CV text, sections, and links
├── Riya_Shrestha_CV.pdf # Pre-rendered 1-page A4 PDF for direct 1-tap download
├── og-image.png         # 1200x630 OpenGraph / LinkedIn / WhatsApp preview card
├── robots.txt           # Search engine crawler directives
├── sitemap.xml          # XML sitemap for riyashrestha.id
├── AGENTS.md            # Project reference and rules for AI agents and developers
├── favicon.svg          # "RS" monogram icon (primary)
├── favicon.png          # 512x512 PNG fallback of the same icon
└── CNAME                # Created by GitHub when the custom domain is saved. Contains: riyashrestha.id
```

> [!IMPORTANT]
> Do **not** delete `CNAME`. Without it the custom domain stops working.

---

## 2a. Single Source of Truth (`CV.md`)

`CV.md` is the **authoritative source of truth** for Riya Shrestha's CV content. Every section, heading, job title, date range, bullet point, skill, certification, and hyperlink in `index.html` mirrors `CV.md`.

### Mandatory rules for using `CV.md`
1. **Fallback for accuracy:** If there is ever any mismatch or discrepancy between `index.html` and `CV.md`, **`CV.md` is the authoritative fallback**. Bring `index.html` back into exact alignment with `CV.md`.
2. **Make changes from `CV.md`:** When the owner asks for a content update, apply the approved change to `CV.md` first (or simultaneously) and propagate the exact wording to `index.html` so the two files never drift apart.
3. **Zero fabrication or meaning changes:** Strictly follow the guidance and wording of `CV.md`. **Never** make unapproved modifications, creative rewrites, or adjustments that alter the meaning, exaggerate scope, or fabricate skills, tools, metrics, or responsibilities.
4. **Thorough discrepancy checks at all times:** Before and after any edit, perform a thorough section-by-section, line-by-line check between `CV.md` and `index.html` (headings, bullet text, British English spelling, punctuation, dates, and URLs) to verify zero discrepancies exist.

---

## 3. How `index.html` and `styles.css` are built

- **Pure CSS in `styles.css`.** An earlier version used the Tailwind CDN and Google Fonts. Both were removed because headless PDF rendering ran out of time and gave a broken 9 page PDF. Keep the repository self contained with zero external network dependencies.
- **Responsive layout (`@media screen`):** Scoped strictly to `@media screen` (`max-width: 768px`, `600px`, and `380px`) so tablet and mobile viewports stack cleanly without affecting `@media print`.
- **Light & Dark Mode (`@media screen`):** Toggled via `html[data-theme="dark"]` (saved in `localStorage` or triggered via `?theme=dark`), strictly scoped to `@media screen` so `@media print` always outputs the light-mode A4 document.
- **SEO & Social Preview:** Includes `<meta name="description">`, canonical link (`https://riyashrestha.id/`), OpenGraph & Twitter Card tags (`og-image.png`), JSON-LD `Person` schema, `robots.txt`, and `sitemap.xml`.
- **Font:** system font stack (`-apple-system, Segoe UI, Roboto, Arial…`).
- **Palette:** slate text (`#0f172a`, `#334155`, `#64748b`), indigo accent (`#4338ca`, `#6366f1`), emerald for the eligibility badge (`#f0fdf4` / `#bbf7d0` / `#14532d`), amber for the scholarship badge.
- **Screen only elements:** anything with class `.no-print` (the top action bar with "Download PDF" and the theme toggle button, plus `.site-footer`) is hidden when printing.

### Page sections (in order)
1. **Header:** name, tagline, and a **2×2 contact grid** (`.contact-matrix`, fixed `92px` columns, `90px` in print). Each item is an icon plus one word linking to its target:
   - Location → Google Maps (Kathmandu) · Phone → `tel:+9779843553911` · Email → `mailto:riyashrestha1599@gmail.com` · LinkedIn → `linkedin.com/in/riya-shrestha-69b6a4194`
   - The full value is shown in the `title` tooltip.
2. **Work eligibility badge** (`.treaty-badge`): green bar, **full width** (`display:flex; width:100%`).
3. Executive Summary
4. Professional Experience: two roles at Nepal Investment Mega Bank Limited (employer name links to `https://www.nimb.com.np/en/personal-banking`).
5. Education: Islington College (links to `https://islington.edu.np/`) and VIT (links to `https://vit.ac.in/`).
6. Core Competencies & Skills: two card grid.
7. Certifications & Interests: ABRSM.

### Print layout (`@media print`)
- `@page { size: A4; margin: 8mm 12mm 7mm 12mm; }`
- Font sizes and spacing are tuned so the CV **fills exactly one A4 page**, with no overflow and no right edge clipping.
- **Any content change can push it onto 2 pages.** Check the page count after every edit (see §5). If it overflows, cut small amounts of `section` / `.job-bullets li` margins or line height inside `@media print`. Don't shrink the base font below roughly 10px.

---

## 4. Content and style rules (agreed with the owner)

| Rule | Detail |
| :--- | :--- |
| Language | **British English** (specialised, rigour, etc.) |
| Em dashes | **Not allowed.** Use a colon or a preposition instead. En dashes (`&ndash;`) are used **only** in date ranges (e.g. `May 2022 – Present`). |
| Job titles | `Junior Officer: Compliance`, `Management Trainee: Compliance` |
| Degrees | `Master of Business Administration (MBA) in Project Management`, `B.Tech (Computer Science and Engineering)` |
| Scholarship | `AAA Scholarship (2026): Awarded for…` |
| Hyphens | Removed from open compounds: account level, account operating, branch level, high risk, red flag, lifecycle, tech enabled, results oriented. Standard terms keep theirs (Cross-Border, Non-Resident, post-activation, end-to-end, World-Check). |
| Wording | "prevent unauthorised or fraudulent reactivation", "undisclosed beneficial ownership", "charge and fee deductions", "anomalous transaction velocity", "five years" |
| Workflow | For text reviews, **list proposed changes first and wait for approval** before editing. |

### Content fidelity fixes (applied 31 Oct 2026)
The CV was checked against the owner's source Markdown and brought back in line with it:
- American spellings fixed: `Scrutinise` (×2), `unauthorised` (×2).
- Removed wording that wasn't in the source: "Politically Exposed Persons (PEP)", "Advanced Excel, Data Analysis", "track resolution metrics", "enforcing corrective action plans", "verified customer identification dossiers", "comprehensive training sessions…".
- Restored source terms: **ECDD** (not EDD), "Excel & Compliance Reporting", "Train newly recruited trainees…", "eligible to work in India".
- Restored the dropped skill "Operational Non-Compliance Identification".
- Removed "Executive Preview" from the screen-only action bar (the print button is kept).

> [!IMPORTANT]
> **Strict Content Integrity:** Do **not** add claims, skills, metrics, or achievements that aren't in `CV.md`, and do **not** alter the meaning of any bullet or section. All content changes require the owner's explicit approval and must be verified against `CV.md` for discrepancies.

> [!NOTE]
> "Associated Board of the Royal Schools of Music" is the official ABRSM name. The source's "Associate Board" was a typo, so keep "Associated".

---

## 5. Generating the PDF

`Riya_Shrestha_CV.pdf` is bundled in the repository for direct 1-tap download. Always regenerate it whenever `index.html` or `styles.css` changes.

**macOS (Google Chrome headless):**

```zsh
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --disable-gpu --no-sandbox \
  --user-data-dir="/tmp/chrome_pdf_profile" --no-pdf-header-footer \
  --print-to-pdf="Riya_Shrestha_CV.pdf" "file://$(pwd)/index.html"
```

**Windows (Microsoft Edge headless with a separate profile directory):**

```powershell
$tempDir = Join-Path $env:TEMP "edge_pdf_profile"
& "C:\Program Files (x86)\Microsoft\Edge\Application\msedge.exe" --headless --disable-gpu --no-sandbox `
  --user-data-dir="$tempDir" --no-pdf-header-footer `
  --print-to-pdf="<output>\Riya_Shrestha_CV.pdf" "file:///<path>/index.html"
```

Check the page count (it must be **1**):

```powershell
$c = [System.IO.File]::ReadAllText("<output>\Riya_Shrestha_CV.pdf")
[regex]::Matches($c, "/Type\s*/Page[^s]").Count
```

Edge logs "Edge LLM: catalog update failed" errors. These are harmless.

---

## 6. Favicon

- `favicon.svg`: 512×512 rounded square, slate to indigo gradient background, white "R" and indigo "S" monogram, indigo underline, small emerald dot in the top right corner.
- `favicon.png`: rendered from the SVG through Edge headless (`--screenshot`, 512×512).
- Linked in `<head>`:
  ```html
  <link rel="icon" type="image/svg+xml" href="favicon.svg">
  <link rel="alternate icon" type="image/png" href="favicon.png">
  ```

---

## 7. Domain and DNS setup

**GitHub:** Settings → Pages → Custom domain = `riyashrestha.id` → Save (this creates `CNAME`). After DNS verifies, tick **Enforce HTTPS**.

**Hostinger DNS records (configured and verified as correct):**

| Type | Name | Content |
| :--- | :--- | :--- |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| CNAME | `www` | `swarupdas02.github.io` |

- The 4 A records are GitHub's anycast/CDN IPs (for redundancy and load balancing). The apex (`@`) can't use a CNAME, which is why it uses A records.
- With a custom domain, GitHub routes by the `Host` header, so the `/riya-shrestha` path isn't needed.

**Last known status:** GitHub showed `DNS check unsuccessful (InvalidDNSError)` and HTTPS was not yet available. The records were correct, so the likely causes were DNS propagation or `.id` domain activation. Suggested fixes: lower the TTL to `300`, confirm the domain is **Active** with Hostinger nameservers, then Remove and re-add the domain in GitHub Pages and click "Check again". **If you pick this up, check this first.**

### Adding more projects on the same domain (free)
- Recommended: use **subdomains** (e.g. `game.riyashrestha.id`). Set that repo's custom domain to it and add a Hostinger `CNAME` with name `game` pointing to `swarupdas02.github.io`.
- Subpaths like `riyashrestha.id/game` from a *different* repo aren't supported natively. Options: a meta refresh redirect page at `/game/index.html` in this repo, or copying the game's build into a `game/` folder here.

---

## 8. Checklist for future edits
1. **Check `CV.md` first:** Treat `CV.md` as the single source of truth. Never fabricate information or alter the meaning of existing points.
2. **Propose before editing:** For any text changes, list the exact proposed changes and wait for the owner's go-ahead.
3. **Follow the style rules in §4:** British English, no em dashes, no unnecessary hyphens in open compounds.
4. **Keep `CV.md` and `index.html` in lockstep:** Update both files together and run a thorough line-by-line check to confirm zero discrepancies between them.
5. **Keep the repository self contained:** Use local `styles.css` only — no CDNs, external stylesheets, or external fonts.
6. **Verify the PDF (§5):** Regenerate `Riya_Shrestha_CV.pdf` and confirm it is **exactly 1 page** with no right-edge clipping.
7. **Check visual alignment:** Confirm the 2×2 header button grid and the full-width green eligibility bar still line up flush with the right edge across desktop, tablet, mobile, and print.
8. **Commit and push:** Commit `CV.md`, `index.html`, `styles.css`, `Riya_Shrestha_CV.pdf`, and `AGENTS.md` (plus any assets) and push. GitHub Pages redeploys in about a minute.
