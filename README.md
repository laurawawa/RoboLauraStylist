# RoboLaura Stylist

A personal wardrobe stylist agent for Laura. Each week it studies the stylists
and critics she trusts, then hunts secondhand and deeply-discounted pieces that
match her taste and quality standards — and delivers a short, verified shortlist
to buy from.

## How it works
The "brain" is plain markdown, so any capable agent runner (Claude or Codex) can
execute it. A scheduler points at `runner-prompt.md`, which reads the other files
and produces a weekly report.

## Folder map
- `personal-style-guide.md` — the hard buying filter (sizes, fabrics, colors,
  brands, price caps, exclusions). Wins all conflicts.
- `sources.md` — the stylist roster: Cassandra Sethi (Next Level Wardrobe),
  itsolgavi, Andrea Cheong, Tinsley Crisp, and Derek Guy — with each one's
  principles, crawl URLs, and how readable they are.
- `output-format.md` — the exact weekly report format.
- `runner-prompt.md` — the master prompt the weekly run executes.
- `scan-log.md` — run history + Laura's feedback (drives future runs).
- `watchlist.md` — standing "in search of" items checked every run (e.g. Leset
  Kyoto in her size) with target offer prices.
- `reports/` — dated weekly reports (`YYYY-MM-DD-scan.md`).
- `archive/` — backup of the original Codex automation (config + full memory).

## Channels searched
Poshmark and eBay (resale) plus retail discounts (Bloomingdale's, Nordstrom
Rack, Saks OFF 5TH, The Outnet). Every recommended listing is individually
verified live before it's suggested.

## Status (2026-06-13)
- ✅ Portable agent definition built; first report delivered (`reports/2026-06-13-scan.md`).
- ⏳ Deferred: weekly scheduler, email delivery, retail-site hardening.
- The legacy Codex weekly cron still runs (path now repaired) and will be retired
  once this runner is proven.

## The feedback loop
After each report, Laura replies yes/no per item plus any direction changes. That
gets logged to `scan-log.md` and tightens the next run. Approved style changes
are written into `personal-style-guide.md`.
