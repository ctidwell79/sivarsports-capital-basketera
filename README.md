# sivarsports-capital-basketera

Public schedule site for **Sivar Sports Academy** at **Capital Basketera 2026** (El Salvador, 28-30 de mayo 2026).

Hosted at: <https://capitalbasketera.sivarsports.com>

## What's in here

| File | Purpose |
|---|---|
| `index.html` | Single-file site. Embeds CSS + JS. No build step. |
| `Capital_Basketera_2026_Team_*.pdf` | 7 parent-handout PDFs (one per team) linked from each team card. |
| `Capital_Basketera_2026_MASTER_Coaches_Handout.pdf` | Internal coaches manual — accessible at `/coaches` or `/manual`. |
| `netlify.toml` | Netlify config (headers, caching, pretty URL redirects). |
| `_redirects` | Pretty per-team URLs (`/u15m` → `#u15m`), PDF shortcuts (`/u15m/pdf`). |
| `robots.txt` + `sitemap.xml` | SEO. |
| `404.html` | Branded not-found page. |

## Features

- **🔴 Live Next Game banner** with second-by-second countdown (switches to "EN VIVO AHORA" during games)
- **Day filter** (Jueves / Viernes / Sábado) + **Team filter** (U11–U17) — combinable
- **Master schedule** (all 27 games + 2 byes, sorted chronologically)
- **Per-team cards** with group rosters, full schedule, WhatsApp share button, PDF download
- **Venue list** with Google Maps pins
- Mobile-responsive (sticky filter bar, touch-friendly pills)
- SSA brand: navy `#1E2D58`, coral `#E8607A`, gold `#F5C518`, Bebas Neue + Inter

## Deploy

### Option A — Drag & drop (fastest)
1. Zip this folder (or just open it in Finder).
2. Go to <https://app.netlify.com/drop>.
3. Drag the folder onto the page.
4. Once it deploys, go to **Site settings → Domain management → Add custom domain** → `capitalbasketera.sivarsports.com`.
5. Add the Netlify-issued CNAME to GoDaddy DNS for `sivarsports.com`.
6. Wait ~5 min for Let's Encrypt cert.

### Option B — GitHub + Netlify (recommended for ongoing updates)
1. Create repo `ctidwell79/sivarsports-capital-basketera` on GitHub.
2. Push this folder as the repo root.
3. In Netlify (Kamay Group team) → **Add new site → Import from Git** → pick this repo.
4. Build settings: leave blank (no build step). Publish dir: `.`
5. Add custom domain `capitalbasketera.sivarsports.com` + DNS CNAME at GoDaddy.

## Updating the schedule

If the tournament organizer changes anything:

1. Edit `cb_data.py` in the parent build folder (`outputs/`).
2. Re-run `python3 build_website.py` — regenerates `capitalbasketera_index.html`.
3. Copy the new HTML to this folder as `index.html`.
4. Run `python3 build_team_pdfs.py` if any team's schedule changed — regenerates the 7 PDFs.
5. Re-run `python3 audit_check.py` to confirm zero errors before pushing.
6. `git commit -am "Update schedule"` and push — Netlify auto-deploys.

## Pretty URLs

These all work after deploy:
- <https://capitalbasketera.sivarsports.com/> — main page
- `/u11`, `/u13f`, `/u13m`, `/u15f`, `/u15m`, `/u17f`, `/u17m` — jump to that team
- `/u15m/pdf` — directly download a team's PDF
- `/coaches` or `/manual` — internal coaches handout

## Tournament dates

- **Jueves** = 2026-05-28
- **Viernes** = 2026-05-29
- **Sábado** = 2026-05-30
- (All times shown are El Salvador time, UTC-6)

If the dates change, update `DAY_DATES` in `cb_data.py` (or in `build_website.py`) and rebuild.

---

**CTC — Campeones Trabajan Como Campeones**

Sivar Sports Academy · ADARS · El Salvador 🇸🇻
