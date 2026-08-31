# Design: Badkamer Renovatie Antwerpen — Audit & Original Rebuild

Date: 2026-08-31
Branch: `seo-rebuild-antwerpen`
Status: approved (approach B)

## 1. Background

The repo is a static mirror of a WordPress/Elementor site,
`badkamerrenovatie.montegava.com`, trading as **Badkamer Renovatie Antwerpen**.
It is one instance of a templated lead-generation microsite network built by
MONTEGAVA, fronting for **Avant Garde Afbouw**, an Amsterdam finishing/afbouw
contractor (Karspeldreef 1275, 1104 SE Amsterdam; stucwerk, schilderwerk,
tegelwerk, vloerverwarming). Sibling microsites exist for Deurne, Merksem,
Borgerhout and Berchem.

### Template-contamination found

- Contact page JSON-LD `Organization`/`WebSite` name = "Badkamer Renovatie **Amsterdam**".
- `/faq` service-area answer lists **Nijmegen** satellite towns (Lent, Wijchen,
  Beuningen, Groesbeek, Arnhem).
- Home FAQ references **Amsterdam** districts/areas (De Pijp, IJburg,
  Zuid/Noord/West/Oost).
- Directory `toilet-renovatie-nijmegen/` — currently a lorem-ipsum 404
  (`noindex`), yet linked in every footer as "Toilet renovatie".
- `/diensten` JSON-LD image caption: "badkamer renovatie nijmegen".
- `<html lang="en-US">` and `og:locale=en_US` on Dutch content.
- Location token concatenation from a broken find/replace:
  "in Antwerpenhangen", "woningen in Antwerpensoms", "AntwerpenZuid", etc.
- Relative `rel=canonical` pointing at `index.html` on every page.
- Multiple `<h1>` on `/diensten` and `/faq`; `<h5>` used as eyebrow labels.
- No `robots.txt`, no `sitemap.xml`.
- Files are UTF-8 **with BOM**; some pre-existing mojibake in meta text
  (`âœ“` for `✓`).

### Verifiability problem (central finding)

Avant Garde Afbouw publishes no years-in-business, certifications, warranty
terms, or review counts, and shows no Antwerp/Belgium presence. Every trust
claim on the current site — "15+ jaar ervaring", "500+ projecten",
"5.0 / 500+ tevreden klanten", "gecertificeerd vakmanschap", "garantie",
KVK 67228275 (Dutch parent, not a Belgian KBO) — is therefore **unverified**.

## 2. Goals

1. Produce the full 18-section strategic audit & rebuild specified by the
   client master prompt.
2. Rebuild the site's real pages with genuinely original, Antwerp-specific,
   conversion-focused content — reconstructed from first principles, not
   synonym-swapped.
3. Remove all cross-city contamination and fix technical SEO defects.
4. Make no unverifiable claim; mark every gap for the business owner.

## 3. Decisions (approved)

| # | Decision |
|---|----------|
| D1 | Target market: **Antwerp, Belgium**. Purge all Amsterdam/Nijmegen traces. |
| D2 | Deliverable: strategy document **and** rebuilt HTML in this repo. |
| D3 | Rebuild depth: **B — in-place restructure** within the Elementor framework (fix heading hierarchy, re-order/add/drop sections per new IA, keep styling). |
| D4 | Facts: default to copy that makes **no unverifiable claim**; insert `[FACT REQUIRED FROM BUSINESS OWNER]` with a precise ask. Infer cautiously from Avant Garde Afbouw only where reasonable. No invented reviews/awards/tenure. |
| D5 | Analysis prose in English; all rebuilt page copy in Belgian/Flemish Dutch. |
| D6 | **Do not** build separate neighbourhood pages here (Deurne/Merksem/Borgerhout/Berchem already exist as external microsites — self-cannibalisation). Use one strong "Werkgebied" section and flag network-wide duplicate-content risk. Reversible if the owner confirms the siblings are being retired. |
| D7 | Create one new real page: `toilet-renovatie-antwerpen/` replacing the broken `toilet-renovatie-nijmegen/` 404. Add a 301-intent note. |
| D8 | Service content: one strong `/diensten` page (no thin per-service URL split) unless the IA section surfaces enough unique content to justify splitting. |

## 4. Scope

### In scope — strategy document (`docs/seo/2026-08-31-...-audit.md` + Artifact)

All 18 sections from the master prompt:
1. Executive Summary
2. Current Website Risk Assessment
3. Complete Page Inventory (table)
4. Content Similarity Assessment (A/B/C/D classification)
5. New Information Architecture
6. Keyword & Search Intent Map
7. Topical Authority Map
8. Page-by-Page Rebuild (strategy + structure + SEO elements + full Dutch
   content + conversion + internal links + schema, per page)
9. Local SEO Strategy
10. Internal Linking Strategy
11. Technical SEO Recommendations (CONFIRMED vs REQUIRES VERIFICATION)
12. UX & Conversion Recommendations
13. Trust / E-E-A-T Recommendations
14. Content Gaps
15. Keep / Rebuild / Merge / Remove / Create
16. Final Website Blueprint (table)
17. Implementation Roadmap (6 phases)
18. Final Quality & Originality Audit (the 10-question test)

### In scope — HTML rebuild

| Page | Action |
|------|--------|
| `index.html` | Rebuild: new hero, restructure sections to new IA, original copy, fix H-hierarchy, rewrite title/meta/OG/JSON-LD, `lang="nl-BE"`, purge claims/contamination, dedupe FAQ (keep 3–4 home-level Q's linking to `/faq`). |
| `diensten/index.html` | Rebuild: single `<h1>`, original service explanations with real process detail, remove verbatim repetition with home, `Service` + `BreadcrumbList` schema. |
| `over-ons/index.html` | Rebuild: honest story (Avant Garde Afbouw as operator, Antwerp focus), remove "500+ / 15+ jaar" unless `[FACT REQUIRED]` filled, real process, team `[FACT REQUIRED]`. |
| `faq/index.html` | Rebuild: single `<h1>`, Antwerp-relevant Q's (permits/VvE/appartementen/bereikbaarheid/BTW 6% vs 21%), valid `FAQPage` schema matching visible text, no duplication of home FAQ wording. |
| `contact/index.html` | Rebuild: fix Amsterdam schema → Antwerp `LocalBusiness`, correct NAP, hours, form labels to Dutch, add `[FACT REQUIRED]` for KBO/BTW-BE, map. |
| `toilet-renovatie-antwerpen/index.html` | **New** real page (replaces Nijmegen 404). Own strategy, structure, schema. Update all footer links. |
| `privacy-policy/`, `algemene-voorwaarden/` | Light pass: entity name, contamination, `lang`, contact block. Flag that legal text needs owner/lawyer review for Belgian consumer law. |
| Site-wide | `robots.txt`, `sitemap.xml`, footer "Werkgebied" block, consistent `Organization`/`LocalBusiness` `@id` graph, breadcrumb schema, image `alt`/captions, internal links. |

### Out of scope

- New neighbourhood pages (D6).
- Rewriting Elementor CSS / visual redesign (C).
- Live server / DNS / hosting / actual 301 config (mark as REQUIRES
  IMPLEMENTATION).
- Legal copy authored to Belgian statute (flag for lawyer).
- Fabricated reviews, ratings, counts, certifications, tenure.

## 5. Constraints & conventions

- Preserve Elementor structure and class names; change text nodes, headings,
  meta, and `<script type="application/ld+json">` blocks only.
- Keep UTF-8 with BOM; write real Unicode (`✓`, `–`, `€`), not entities where
  the file already uses raw Unicode.
- `lang="nl-BE"`, `og:locale="nl_BE"`.
- Canonicals: absolute `https://badkamerrenovatie.montegava.com/<path>/`.
- Dutch copy: Belgian usage (BTW not btw-NL rates; "u" register consistent per
  page; "gratis vrijblijvende plaatsbezoek" acceptable BE phrasing).
- Every unverifiable claim → removed or `[FACT REQUIRED FROM BUSINESS OWNER: …]`.
- Originality: each rebuilt page must pass the §18 ten-question test; headings,
  argument order, examples, CTAs independently developed (not the template's
  4-step / 3-service skeleton reproduced).

## 6. Acceptance criteria

1. Strategy doc contains all 18 sections; every table populated; no "TBD".
2. Every `[FACT REQUIRED]` marker names the specific fact and where it goes.
3. `grep -ri "amsterdam\|nijmegen\|lent\|wijchen\|beuningen\|groesbeek\|arnhem\|de pijp\|ijburg"` over `*.html` returns nothing outside intentional context.
4. No `lang="en-US"` / `og:locale=en_US` remain; no concatenated
   "Antwerpen<word>" tokens remain.
5. Each rebuilt page: exactly one `<h1>`; logical H2/H3 nesting; JSON-LD parses
   and matches visible content.
6. `toilet-renovatie-antwerpen/` exists, is `index,follow`, linked in footers;
   `toilet-renovatie-nijmegen/` handled (removed + redirect note).
7. `robots.txt` + `sitemap.xml` present and internally consistent.
8. No claim of reviews, ratings, project counts, years, or certifications that
   isn't backed by a filled `[FACT REQUIRED]` or a cited source.
9. Home and `/faq` share no verbatim FAQ answers.
10. Work committed on `seo-rebuild-antwerpen` in reviewable page-by-page commits.

## 7. Risks

| Risk | Mitigation |
|------|-----------|
| Editing Elementor soup breaks layout | Text/heading/meta/JSON-LD only; diff-review each page; no structural node deletion beyond whole `.elementor-section` blocks that are cleanly bounded. |
| BOM / encoding corruption | Verify with `file` after each write; keep BOM. |
| "Originality" still echoes template | Run §18 test per page before commit; rework sections that fail. |
| Owner can't supply facts → claims must go | Copy is written to stand without them; markers make the cost of omission explicit. |
| Network duplicate content unaddressable from one repo | Document as a cross-site risk owner/agency must resolve (canonical or differentiation across the network). |

## 8. Sequence

1. Strategy doc §1–18 → commit → publish Artifact.
2. HTML: `index` → `diensten` → `over-ons` → `faq` → `contact` →
   `toilet-renovatie-antwerpen` (new) → legal pages (light).
3. Site-wide: internal links, footer, schema graph, `robots.txt`,
   `sitemap.xml`, image alt/captions.
4. Final verification pass against §6; originality pass against §18.
