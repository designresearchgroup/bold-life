# The Bold Life

A single-page platform for **The Bold Life** — *Career Reinvention & Leadership
Coaching for Ambitious Women*, founded by **Jamesyn (Jamie) Snitker**, ICF
Professional Certified Coach (PCC). Woman-Owned Small Business.

**The Bold Life's own brand system** — burgundy (`#DC343B`) + black, Poppins (body)
and Montserrat (display), square corners, women-led — matching her live site
`theboldlife.coach`. The HumanData DS v4 component architecture is used only as the
structural scaffold (grids, cards, rules); a brand-token layer at the top of the page
`<style>` overrides every colour and font so the identity is entirely hers. No blue.
Mobile-first and accessible.

- **Live (GitHub Pages):** set after first deploy — see *Deploy* below.
- **Intended domain:** `theboldlifecoaching.com` (not yet registered).

## Two tracks

1. **B2G** — Leadership development and executive coaching for **government agencies**
   in Arizona and California. Woman-Owned Small Business, ICF-PCC, registered on the
   Arizona Procurement Portal and Cal eProcure (SBE pending, DVBE pursuing).
2. **B2C** — 1:1 **career-reinvention coaching** for ambitious women: the 12-week
   program, the Career Signals assessment, the Clarity Map, and the podcast.

## What's here

```
index.html          The whole site (DS v4 stylesheet embedded inline — self-contained)
img/favicon.svg     "TBL" accent mark
img/og.png          1200×630 social share card (LinkedIn/Slack/iMessage preview)
robots.txt
sitemap.xml
.github/workflows/deploy.yml   CI/CD → GitHub Pages
```

It's a static page — **no build step**. Edit `index.html` and push.

## Deploy (CI/CD)

Push to `main`. GitHub Actions publishes the repo to GitHub Pages. The workflow runs
sanity checks first (og image present, canonical present, the honesty caveat intact,
and **no unbacked promotion/outcome rate** on the page), then deploys.
`workflow_dispatch` re-runs a deploy without a commit.

One-time setup on the repo: **Settings → Pages → Build and deployment → Source:
GitHub Actions.** (The `gh` commands used to create this repo already set this.)

## Custom domain (`theboldlifecoaching.com`)

Do this once the domain is registered:

1. Add a `CNAME` file at the repo root containing one line: `theboldlifecoaching.com`
   (and commit it), **or** set it under Settings → Pages → Custom domain.
2. At the registrar, point DNS at GitHub Pages:
   - Apex `@`: four A records → `185.199.108.153`, `185.199.109.153`,
     `185.199.110.153`, `185.199.111.153` (and matching AAAA records for IPv6).
   - `www`: a CNAME → `designresearchgroup.github.io`.
3. Wait for DNS, then tick **Enforce HTTPS** in Settings → Pages.
4. Set up email for the booking address on the page so the CTA actually receives mail.

Until the domain is live, the site serves from the GitHub Pages URL and every
link/preview still works.

## Contact / booking

The CTAs currently point to `hello@theboldlifecoaching.com` as a placeholder. **Swap
in Jamesyn's real working email** (two spots in `index.html` — the contact block and
the footer — plus the mailto in the nav) so inquiries land before the domain is live.

## Design system

Two layers, in order, inside `index.html`:

1. **DS v4 scaffold** — the HumanData DS v4 stylesheet, embedded verbatim, used only
   for structure (grid/card/rule components, spacing, responsive rules).
2. **The Bold Life brand layer** — the first block of the page `<style>` overrides the
   DS colour and font tokens: `--accent:#DC343B` (brand red), Poppins + Montserrat,
   and a warm burgundy→wine→rose `data-tint` family. **No HumanData blue.**

Keep brand changes in that brand layer, never in the DS block, so the scaffold stays a
clean, swappable base. Source of truth for the brand itself is `theboldlife.coach`
(red `#DC343B`, ink `#1A1A1A`, Poppins body, Montserrat display).

## Honesty note (important)

Per project policy, the page publishes only what can be backed:

- Credentials and registrations are current or **clearly marked in progress**
  (SBE *pending*, DVBE *pursuing*, CMAS *ready to pursue*, federal GSA/WOSB *roadmap*).
- The **"85% promotion rate"** figure from early positioning is **not on the page** —
  it needs documented data before it is used. CI fails the build if a promotion/outcome
  rate sneaks in.
- No fabricated testimonials or client logos. No guarantee of a specific outcome.
