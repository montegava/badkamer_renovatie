# Badkamer Renovatie Antwerpen — Audit & Rebuild Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Produce the 18-section strategic audit and rebuild the site's real HTML pages with original, Antwerp-specific, claim-safe content, removing all cross-city template contamination.

**Architecture:** Two deliverables from one branch. (1) A strategy document authored as Markdown in `docs/seo/` and published as an Artifact. (2) In-place edits to the existing WordPress/Elementor static HTML — text nodes, headings, meta, and JSON-LD only — plus one new page directory and site-wide `robots.txt`/`sitemap.xml`. No build system, no test runner; verification is grep assertions, JSON-LD parse checks, and the spec's §6 acceptance criteria + §18 originality test.

**Tech Stack:** Static HTML (Elementor output), JSON-LD, Markdown, Python 3.14 (available as `python`, used only for extraction/validation scripts in scratchpad), git.

## Global Constraints

- Target market: **Antwerp, Belgium**. No Amsterdam/Nijmegen/Lent/Wijchen/Beuningen/Groesbeek/Arnhem/De Pijp/IJburg references outside intentional context (e.g. naming Badkamer Verbouwen's real Amsterdam HQ in the audit).
- Analysis prose: **English**. All rebuilt page copy: **Belgian/Flemish Dutch**.
- `lang="nl-BE"`, `og:locale="nl_BE"` on every rebuilt page.
- Canonicals: absolute `https://badkamerrenovatie.montegava.com/<path>/`.
- Files stay **UTF-8 with BOM**; write raw Unicode (`✓ – € é`), not HTML entities, where the file already uses raw Unicode. Verify with `file <path>` after each write.
- Preserve Elementor structure and class names. Change only text nodes, heading tags/levels, `<meta>`, `<title>`, `<html lang>`, and `<script type="application/ld+json">`. Delete whole cleanly-bounded `.elementor-section` blocks only.
- No claim of reviews, ratings, project counts, years in business, certifications, awards, partnerships, or guarantees unless backed by a filled `[FACT REQUIRED FROM BUSINESS OWNER: …]` marker or a cited source. Default copy must read well with the claim absent.
- Each rebuilt page: exactly one `<h1>`; logical H2/H3 nesting; JSON-LD must parse and match visible content.
- Do not reproduce the template's 4-step process skeleton or 3-service triad as-is; headings, argument order, examples and CTAs independently developed.
- Commit per task on branch `seo-rebuild-antwerpen`.

Reference: full findings, decisions D1–D8, scope, and acceptance criteria in
`docs/superpowers/specs/2026-08-31-badkamer-renovatie-antwerpen-audit-rebuild-design.md`.

---

## File Structure

| Path | Responsibility |
|------|----------------|
| `scratchpad/inventory.md` (scratchpad dir) | Raw extracted data for audit tables — not committed. |
| `docs/seo/2026-08-31-badkamer-renovatie-antwerpen-audit.md` | The 18-section strategy document (committed + published as Artifact). |
| `index.html` | Home — rebuilt. |
| `diensten/index.html` | Services — rebuilt. |
| `over-ons/index.html` | About — rebuilt. |
| `faq/index.html` | FAQ — rebuilt. |
| `contact/index.html` | Contact — rebuilt (schema Amsterdam→Antwerp). |
| `toilet-renovatie-antwerpen/index.html` | **New** page, replaces `toilet-renovatie-nijmegen/`. |
| `toilet-renovatie-nijmegen/` | Removed; redirect documented in audit §11. |
| `privacy-policy/index.html`, `algemene-voorwaarden/index.html` | Light pass only. |
| `robots.txt`, `sitemap.xml` | New site-wide files. |
| `img/` | Rename/re-caption `badkamer-renovatie-antwerpen-*` stay; fix `alt`/JSON-LD captions referencing "nijmegen". |

---

## Task 1: Raw inventory extraction

**Files:**
- Create: `<scratchpad>/inventory.md`
- Use: `<scratchpad>/extract.py` (already written this session)

- [ ] **Step 1: Extract every page's SEO surface**

Run for all 8 HTML files (`index`, `diensten`, `over-ons`, `faq`, `contact`, `privacy-policy`, `algemene-voorwaarden`, `toilet-renovatie-nijmegen`):
```
cd "d:/tortocake/badkamer_renovatie" && python "<scratchpad>/extract.py" <files...> > "<scratchpad>/raw_extract.txt"
```

- [ ] **Step 2: Record per-page rows**

Into `<scratchpad>/inventory.md`, one block per URL capturing: current title, meta description, canonical, H1, full H2/H3 list, JSON-LD types present, approx word count (`wc -w` on extracted TEXT block), internal links out, external links out, primary topic, search intent, main CTA, and every contamination string found (with line context).

- [ ] **Step 3: Diff home vs /faq FAQ answers**

List which Q&A pairs are byte-identical or near-identical between `index.html` and `faq/index.html`. Record verbatim.

- [ ] **Step 4: Catalogue template artifacts**

Grep the repo and record each hit with file:line —
```
grep -rniE "amsterdam|nijmegen|lent|wijchen|beuningen|groesbeek|arnhem|de pijp|ijburg" --include=*.html .
grep -rniE "lang=\"en-US\"|og:locale.{0,10}en_US" --include=*.html .
grep -rniE "Antwerpen[a-z]" --include=*.html .
grep -rniE "15\+? *jaar|500\+|5\.0|gecertificeerd|KVK" --include=*.html .
```

- [ ] **Step 5: No commit** (scratchpad only). Confirm `inventory.md` has 8 page blocks + artifact catalogue.

**Verification:** `inventory.md` lists all 8 pages and every grep above has its hits transcribed.

---

## Task 2: Strategy doc §1–§7 (assessment + maps)

**Files:**
- Create: `docs/seo/2026-08-31-badkamer-renovatie-antwerpen-audit.md`

**Interfaces:**
- Consumes: `<scratchpad>/inventory.md` from Task 1.
- Produces: doc file with sections 1–7 complete; page IDs (`P1`–`Pn`) and
  proposed URL slugs that Tasks 3–4 and 6–11 reference.

- [ ] **Step 1: Write header + §1 Executive Summary**

3–5 short paragraphs: what the site is, the network/contamination problem, the verifiability problem (operator = Badkamer Verbouwen, Amsterdam afbouw contractor, no Antwerp track record published), the recommended path (rebuild for genuine Antwerp relevance, strip unverifiable claims), expected outcome.

- [ ] **Step 2: Write §2 Current Website Risk Assessment**

Rank risks: (a) cross-city contamination visible to users + Google, (b) unverifiable trust claims (advertising-law and E-E-A-T exposure), (c) network duplicate content across sibling microsites, (d) technical defects (relative canonicals, `en-US`, multiple H1, lorem-ipsum indexnofollowed page linked sitewide, no sitemap/robots), (e) thin/duplicated copy. Each: severity, why it matters, who it hurts.

- [ ] **Step 3: Write §3 Complete Page Inventory**

One Markdown table, one row per existing URL, columns from the master prompt §3 (URL, type, title, meta, H1, H2/H3 summary, primary topic, intent, primary kw, secondary kw, location modifiers, main CTA, internal links, schema, word count, conversion purpose, info purpose, duplicate/thin flag, cannibalization flag, copied-section flag, quality issues, missing info, trust issues, UX issues, SEO issues). Populate from `inventory.md`.

- [ ] **Step 4: Write §4 Content Similarity Assessment**

Table classifying each major section of each page A (keep) / B (rebuild) / C (remove) / D (replace with real business info), with a one-line reason. Explicitly name the template skeletons (4-step process, 3-service triad, shared FAQ) and the cross-city passages.

- [ ] **Step 5: Write §5 New Information Architecture**

Main nav, page hierarchy, and for each proposed page: why it exists, who it serves, intent, primary topic, conversion goal, how it differs from siblings, internal-linking role. Resolve decision D8 here (one `/diensten` vs split) with the reasoning. Assign `P1…Pn` IDs + final slugs.

- [ ] **Step 6: Write §6 Keyword & Search Intent Map**

Table: page | primary keyword | secondary keywords | semantic entities | intent | geo modifiers | related questions. Belgian phrasing ("badkamer renoveren Antwerpen", "badkamerrenovatie prijs", "inloopdouche plaatsen Antwerpen", "renovatie badkamer appartement", "BTW 6% renovatie woning"). Note consolidation/canonical/removal calls where intents collide.

- [ ] **Step 7: Write §7 Topical Authority Map**

Core / supporting / educational / commercial / local topic clusters. Per topic: intent, target page, primary theme, supporting keywords, internal links, "new page justified? y/n + why". Keep the count small; no low-value page farm.

- [ ] **Step 8: Commit**

```
git add docs/seo/2026-08-31-badkamer-renovatie-antwerpen-audit.md
git commit -m "Add audit sections 1-7: risk, inventory, similarity, IA, keyword & topical maps"
```

**Verification:** §1–7 present; §3 table has a row per existing URL; §4 covers every page; §5 assigns page IDs + slugs used downstream; no "TBD".

---

## Task 3: Strategy doc §8 — page-by-page rebuild content

**Files:**
- Modify: `docs/seo/2026-08-31-badkamer-renovatie-antwerpen-audit.md`

**Interfaces:**
- Consumes: page IDs + slugs from §5.
- Produces: for every page ID, the full sub-block (A Strategy, B Structure,
  C SEO elements, D Full original Dutch content, E Conversion, F Internal
  linking, G Schema) that Tasks 6–11 copy into the HTML.

- [ ] **Step 1: Home (`P1`)** — write A–G. D = complete Dutch page copy: hero (H1 `Badkamer renovatie in Antwerpen`), one intro that says something concrete (scope of works: sloop, leidingwerk, waterdichting, tegelwerk, sanitair, ventilatie, verlichting, afwerking), how the project is run (één aanspreekpunt, vaste ploeg, planning vooraf), what's decided at the plaatsbezoek, a differentiated "werken in Antwerpse woningen" block (rijhuizen/herenhuizen, appartementen + syndicus/VME, betonvloeren, oude gietijzeren afvoer), 3–4 home-level FAQ (distinct wording from `/faq`), CTA. No project counts / ratings / years unless `[FACT REQUIRED]` filled. C: title ≤60 chars, meta ≤155, slug `/`, canonical absolute, OG. G: `WebPage` + `LocalBusiness` (+ `BreadcrumbList`).

- [ ] **Step 2: Diensten (`P2`)** — A–G. Single H1 `Onze diensten voor badkamerrenovatie in Antwerpen`. D: three services with real substance (what's included, typical sequence, decisions the client makes, what affects price) — no verbatim reuse of the home wording. G: `Service` × n + `BreadcrumbList`.

- [ ] **Step 3: Over ons (`P3`)** — A–G. Honest narrative: operated by Badkamer Verbouwen (afbouwspecialist, tegelwerk/vloerverwarming/stucwerk core competencies — a legitimate strength for bathroom work), focus on Antwerp, how the team works. `[FACT REQUIRED]` markers for: year first Antwerp project, number of Antwerp bathrooms completed, team names/roles, vakman qualifications, warranty length. No "500+/15 jaar" unless filled.

- [ ] **Step 4: FAQ (`P4`)** — A–G. Single H1. 8–10 Antwerp-relevant Q&A, distinct wording from home: BTW 6% vs 21% (renovatie woning >10 jaar), stedenbouwkundige vergunning / melding voor badkamer, appartement + VME-reglement + syndicus toestemming, bereikbaarheid smalle straten / parkeervergunning werfzone stad Antwerpen, asbestattest (woningen < 2001 bij verkoop / sloop), duur, kan de badkamer gebruikt worden, waterdichtheid/garantie, wat kost het (ranges only if `[FACT REQUIRED]` filled — else explain drivers). G: `FAQPage` matching visible text exactly.

- [ ] **Step 5: Contact (`P5`)** — A–G. D: NAP block (Antwerp address, +32 number, hours), what to expect after contact, form field labels in Dutch (Naam, Telefoon, E-mail, Bericht). `[FACT REQUIRED]` for KBO-nummer, BTW BE-nummer, exact vestigingsadres if the Van Lissumstraat 45 address is not real. G: `LocalBusiness` with Antwerp `address`, `areaServed`, `openingHours`, `telephone` — **no** `aggregateRating` unless `[FACT REQUIRED]` filled.

- [ ] **Step 6: Toilet renovatie Antwerpen (`P6`, new)** — A–G. D: full page — scope (toilet, inbouwreservoir, tegelwerk, fonteintje, ventilatie, vloer), combineren met badkamer, kleine-ruimte oplossingen, duur, prijsdrivers. C: slug `/toilet-renovatie-antwerpen/`, `index,follow`. G: `Service` + `BreadcrumbList`. Note: `/toilet-renovatie-nijmegen/` to be removed + 301'd (record in §11).

- [ ] **Step 7: Legal pages (`P7`, `P8`)** — note in §8 that these get a light pass only (entity name, contamination, `lang`, contact block) and a recommendation that a lawyer review them against Belgian consumer/market-practices law (WER Boek VI) and GDPR.

- [ ] **Step 8: Commit**

```
git add docs/seo/2026-08-31-badkamer-renovatie-antwerpen-audit.md
git commit -m "Add audit section 8: full page-by-page rebuild content (Dutch copy + SEO + schema)"
```

**Verification:** every page ID from §5 has A–G; all D copy is Dutch and free of unverifiable claims (or uses `[FACT REQUIRED]`); every `[FACT REQUIRED]` names the fact + its placement; run the §18 ten-question test mentally on each D block, note pass.

---

## Task 4: Strategy doc §9–§18

**Files:**
- Modify: `docs/seo/2026-08-31-badkamer-renovatie-antwerpen-audit.md`

- [ ] **Step 1: §9 Local SEO Strategy** — whether location pages are justified (per D6: no thin wijk pages while siblings live; recommend one Werkgebied section + resolve network duplication via cross-site canonical or real differentiation). GBP/Google Bedrijfsprofiel recommendation, NAP consistency, local entities (Antwerpse wijken as content context not doorway pages), Belgian directories (unizo, trustoo/bouw, Google).

- [ ] **Step 2: §10 Internal Linking Strategy** — table: source page → target page → anchor (Dutch, varied, non-exact-match-stuffed). Include hub/spoke (home ↔ diensten ↔ toilet-renovatie ↔ faq ↔ contact) and contextual links.

- [ ] **Step 3: §11 Technical SEO** — each item tagged `CONFIRMED ISSUE` or `REQUIRES TECHNICAL VERIFICATION`. Covers: relative canonicals, `en-US`, multiple H1, lorem-ipsum noindex page linked sitewide, missing `robots.txt`/`sitemap.xml`, BOM/mojibake, image filenames/alt, `toilet-renovatie-nijmegen` → `toilet-renovatie-antwerpen` **301** (server-side, mark REQUIRES IMPLEMENTATION), trailing-slash consistency, `Organization` `@id` graph split across Amsterdam/Antwerp names.

- [ ] **Step 4: §12 UX & Conversion** — per-page: is purpose clear, is CTA obvious, is trust sufficient, scannability, mobile, buried info. Concrete fixes.

- [ ] **Step 5: §13 Trust / E-E-A-T** — the core recommendation: supply real proof or remove claims. Enumerate every current claim and its status. List legitimate signals available now (Badkamer Verbouwen tegel/vloerverwarming competency, KVK of parent, transparent process, clear NAP) vs. `[FACT REQUIRED]` signals (named reviews + source, project photos with location/date, warranty in writing, KBO registration, team bios, insurance).

- [ ] **Step 6: §14 Content Gaps** — missing commercial pages, informational content, trust content, local content, conversion content — each prioritized by business value × intent × usefulness × ranking realism.

- [ ] **Step 7: §15 Keep / Rebuild / Merge / Remove / Create** — categorized list with one-line rationale each.

- [ ] **Step 8: §16 Final Website Blueprint** — the master-prompt table: Page | URL | Search Intent | Primary Topic | Primary Keyword | Purpose | Priority.

- [ ] **Step 9: §17 Implementation Roadmap** — Phases 1–6 from the master prompt; each task with Priority / Expected benefit / Difficulty / Dependencies / Recommended action.

- [ ] **Step 10: §18 Final Quality & Originality Audit** — run the 10 questions against each rebuilt page's §8 content; record pass/fail + any rework done.

- [ ] **Step 11: Commit**

```
git add docs/seo/2026-08-31-badkamer-renovatie-antwerpen-audit.md
git commit -m "Add audit sections 9-18: local SEO, linking, technical, UX, EEAT, gaps, blueprint, roadmap, originality"
```

**Verification:** all 18 sections present; §11 every item tagged CONFIRMED/REQUIRES; §16 table populated; §18 covers every rebuilt page.

---

## Task 5: Publish strategy doc as Artifact

**Files:**
- Create: `<scratchpad>/audit-artifact.html`

- [ ] **Step 1:** Load the `artifact-design` skill.
- [ ] **Step 2:** Author `audit-artifact.html` — the full audit as a navigable single page (sticky section nav, readable tables with horizontal scroll containers, theme-aware tokens per the Artifact rules). `<title>Antwerp Badkamer Audit</title>`.
- [ ] **Step 3:** Publish via Artifact tool (`favicon` `🛁`, one-sentence `description`).
- [ ] **Step 4:** Paste the Artifact URL into the top of the Markdown doc; commit.

```
git add docs/seo/2026-08-31-badkamer-renovatie-antwerpen-audit.md
git commit -m "Link published audit Artifact"
```

**Verification:** Artifact publishes; URL in the Markdown doc; no horizontal body scroll.

---

## Task 6: Rebuild `index.html`

**Files:**
- Modify: `index.html`

**Interfaces:**
- Consumes: §8 `P1` block (A–G).

- [ ] **Step 1:** Set `<html lang="nl-BE">`; `og:locale` → `nl_BE`; `rel=canonical` → `https://badkamerrenovatie.montegava.com/`; update `<title>` and `<meta name="description">` from §8 `P1` C.
- [ ] **Step 2:** Replace hero `<h1>` + subhead + the three feature labels with §8 copy. Ensure single `<h1>`.
- [ ] **Step 3:** Replace each content `.elementor-section` text block with the corresponding §8 D section; drop the template "4 stappen" section if §8 B removed it, or re-author its headings/copy if kept. Fix all `Antwerpen<word>` concatenations.
- [ ] **Step 4:** Reduce the on-page FAQ to the §8 home-level set; ensure wording differs from `faq/index.html`.
- [ ] **Step 5:** Rewrite the two JSON-LD blocks: `WebPage`+`WebSite`+`Organization` graph with consistent name "Badkamer Renovatie Antwerpen", `inLanguage` `nl-BE`; `FAQPage` matching the reduced visible FAQ exactly; remove any `Amsterdam`/`en-US`; `aggregateRating` only if `[FACT REQUIRED]` filled.
- [ ] **Step 6:** Update footer "Werkgebied" + menu (see Task 11 for the shared footer change; if done first, leave a note).
- [ ] **Step 7: Verify**

```
file index.html                        # UTF-8 (with BOM)
grep -c "<h1" index.html               # expect 1
grep -niE "amsterdam|nijmegen|en-US|Antwerpen[a-z]" index.html   # expect no unintended hits
python -c "import json,re,sys;[json.loads(m) for m in re.findall(r'<script type=\"application/ld\+json\">(.*?)</script>', open('index.html',encoding='utf-8').read(), re.S)]" && echo "JSON-LD OK"
```

- [ ] **Step 8: Commit** `git add index.html && git commit -m "Rebuild home: original Antwerp copy, fixed schema, nl-BE, claim-safe"`

**Verification:** all Step 7 checks pass; visual copy matches §8 `P1` D.

---

## Task 7: Rebuild `diensten/index.html`

**Files:**
- Modify: `diensten/index.html`

- [ ] **Step 1:** `lang`/`og:locale`/canonical (`…/diensten/`)/title/meta per §8 `P2` C.
- [ ] **Step 2:** Collapse to a single `<h1>`; demote the stray second `<h1>` to `<h2>`.
- [ ] **Step 3:** Replace the three service descriptions with §8 `P2` D (substantive, non-duplicative of home).
- [ ] **Step 4:** JSON-LD: `Service` entries (one per service, `provider` = the Organization `@id`, `areaServed` = Antwerpen) + `BreadcrumbList`; fix image caption "nijmegen"→"Antwerpen"; `inLanguage` `nl-BE`.
- [ ] **Step 5: Verify** (same grep/`file`/JSON-LD trio as Task 6, on `diensten/index.html`; `grep -c "<h1"` → 1).
- [ ] **Step 6: Commit** `git commit -m "Rebuild diensten: single H1, substantive service copy, Service schema"`

---

## Task 8: Rebuild `over-ons/index.html`

**Files:**
- Modify: `over-ons/index.html`

- [ ] **Step 1:** `lang`/`og:locale`/canonical (`…/over-ons/`)/title/meta per §8 `P3` C.
- [ ] **Step 2:** Replace body with §8 `P3` D honest narrative; insert `[FACT REQUIRED …]` markers verbatim where §8 specifies.
- [ ] **Step 3:** Remove the "0+ jaar Ervaring" counter and "500+ Renovaties" block, or convert to `[FACT REQUIRED]`.
- [ ] **Step 4:** JSON-LD `AboutPage`/`WebPage` + `Organization` (+ `BreadcrumbList`), consistent name, `nl-BE`.
- [ ] **Step 5: Verify** (trio + `grep -niE "500\+|15\+? *jaar|gecertificeerd"` → only inside `[FACT REQUIRED]` context).
- [ ] **Step 6: Commit** `git commit -m "Rebuild over-ons: honest operator narrative, claims gated behind FACT REQUIRED"`

---

## Task 9: Rebuild `faq/index.html`

**Files:**
- Modify: `faq/index.html`

- [ ] **Step 1:** `lang`/`og:locale`/canonical (`…/faq/`)/title/meta per §8 `P4` C.
- [ ] **Step 2:** Single `<h1>`; replace all Q&A with §8 `P4` D set (Antwerp-specific; wording distinct from home).
- [ ] **Step 3:** Remove the Nijmegen service-area answer entirely; replace with an Antwerp `areaServed` answer.
- [ ] **Step 4:** `FAQPage` JSON-LD regenerated to match the new visible Q&A **exactly**; `nl-BE`.
- [ ] **Step 5: Verify** trio; plus: extract visible questions and JSON-LD `Question` names, assert equal set.
- [ ] **Step 6: Commit** `git commit -m "Rebuild faq: Antwerp-specific Q&A, schema matches visible text, no cross-city"`

---

## Task 10: Rebuild `contact/index.html`

**Files:**
- Modify: `contact/index.html`

- [ ] **Step 1:** `lang`/`og:locale`/canonical (`…/contact/`)/title/meta per §8 `P5` C.
- [ ] **Step 2:** Replace every `Organization`/`WebSite`/`ContactPage` JSON-LD `name` "…Amsterdam" → "Badkamer Renovatie Antwerpen"; set `LocalBusiness` with Antwerp `address`, `telephone` `+32491980272`, `openingHours` `Mo-Su 08:00-17:00`, `areaServed` Antwerpen; remove `aggregateRating` unless `[FACT REQUIRED]` filled.
- [ ] **Step 3:** Dutch form labels; NAP block; add `[FACT REQUIRED: KBO-nummer]`, `[FACT REQUIRED: BTW BE-nummer]`, `[FACT REQUIRED: bevestig vestigingsadres]`.
- [ ] **Step 4:** Replace mojibake `�`/`âœ“` runs with real `✓`/`·`.
- [ ] **Step 5: Verify** trio; `grep -ni "amsterdam" contact/index.html` → none.
- [ ] **Step 6: Commit** `git commit -m "Rebuild contact: Antwerp LocalBusiness schema, correct NAP, Dutch labels"`

---

## Task 11: New `toilet-renovatie-antwerpen/`, remove Nijmegen page, fix footer

**Files:**
- Create: `toilet-renovatie-antwerpen/index.html`
- Delete: `toilet-renovatie-nijmegen/index.html` (and dir)
- Modify: `index.html`, `diensten/index.html`, `over-ons/index.html`, `faq/index.html`, `contact/index.html`, `privacy-policy/index.html`, `algemene-voorwaarden/index.html` (footer links)

- [ ] **Step 1:** Copy `faq/index.html` as the structural shell for the new page (same header/footer/Elementor chrome), strip its body content.
- [ ] **Step 2:** Insert §8 `P6` content: single `<h1>`, sections, CTA; `lang="nl-BE"`; canonical `…/toilet-renovatie-antwerpen/`; title/meta from §8 `P6` C; `robots` `index,follow`.
- [ ] **Step 3:** JSON-LD `Service` + `BreadcrumbList` + `Organization`, `nl-BE`.
- [ ] **Step 4:** In all 7 pages, change footer/menu link `…/toilet-renovatie-nijmegen/` → `…/toilet-renovatie-antwerpen/` and anchor text to "Toilet renovatie Antwerpen". Update the "Werkgebied" block: replace the external sibling-microsite links with plain-text Antwerp wijk names (Deurne, Berchem, Borgerhout, Merksem, Wilrijk, Antwerpen-Zuid) — no outbound links to competitors-in-network unless owner confirms.
- [ ] **Step 5:** `git rm -r toilet-renovatie-nijmegen`.
- [ ] **Step 6: Verify**

```
grep -rl "toilet-renovatie-nijmegen" . --include=*.html   # expect none
grep -rl "toilet-renovatie-antwerpen" . --include=*.html   # expect all 8
file toilet-renovatie-antwerpen/index.html
grep -c "<h1" toilet-renovatie-antwerpen/index.html        # expect 1
```

- [ ] **Step 7: Commit** `git commit -m "Replace lorem-ipsum toilet-renovatie-nijmegen 404 with real toilet-renovatie-antwerpen page; fix footer links"`

---

## Task 12: Legal pages light pass

**Files:**
- Modify: `privacy-policy/index.html`, `algemene-voorwaarden/index.html`

- [ ] **Step 1:** `lang="nl-BE"`; `og:locale`; canonical absolute; title case fix ("privacy policy" → "Privacybeleid").
- [ ] **Step 2:** Replace any `Amsterdam`/cross-city strings; fix `Antwerpen<word>` concatenations; update contact/entity block to the Antwerp NAP + `[FACT REQUIRED: KBO-nummer]`.
- [ ] **Step 3:** Add a visible top note: `[FACT REQUIRED: laat deze tekst juridisch nakijken tegen WER Boek VI (marktpraktijken) en de GDPR — huidige tekst is een template]`.
- [ ] **Step 4:** JSON-LD name consistency + `nl-BE`.
- [ ] **Step 5: Verify** trio on both files; `grep -ni "amsterdam" privacy-policy/index.html algemene-voorwaarden/index.html` → none.
- [ ] **Step 6: Commit** `git commit -m "Legal pages: nl-BE, entity/contamination fixes, lawyer-review markers"`

---

## Task 13: Site-wide — robots.txt, sitemap.xml, schema graph, images

**Files:**
- Create: `robots.txt`, `sitemap.xml`
- Modify: any `img` `alt`/JSON-LD captions still saying "nijmegen"; all pages' `Organization` `@id`

- [ ] **Step 1:** `robots.txt` —
```
User-agent: *
Allow: /
Sitemap: https://badkamerrenovatie.montegava.com/sitemap.xml
```
- [ ] **Step 2:** `sitemap.xml` — `<urlset>` with the 8 canonical URLs (home, diensten, over-ons, faq, contact, toilet-renovatie-antwerpen, privacy-policy, algemene-voorwaarden), `lastmod` = today, absolute HTTPS, trailing slashes.
- [ ] **Step 3:** Grep every page for `"@type":"Organization"` blocks; make `name`, `@id` (`https://badkamerrenovatie.montegava.com/#organization`), `url`, `logo`, `inLanguage` identical across all pages.
- [ ] **Step 4:** `grep -rni "nijmegen\|caption\":\"badkamer renovatie nijmegen" --include=*.html .` → fix remaining alt/caption text to "badkamerrenovatie Antwerpen".
- [ ] **Step 5: Verify**

```
python -c "import xml.dom.minidom;xml.dom.minidom.parse('sitemap.xml')" && echo "sitemap OK"
grep -rni "nijmegen\|amsterdam" --include=*.html . | grep -v "Badkamer Verbouwen\|Karspeldreef"   # expect none
```

- [ ] **Step 6: Commit** `git commit -m "Add robots.txt + sitemap.xml; unify Organization schema; fix image captions"`

---

## Task 14: Final verification + originality pass

**Files:**
- Modify: `docs/seo/2026-08-31-badkamer-renovatie-antwerpen-audit.md` (append a "Verification log" appendix)

- [ ] **Step 1:** Run every §6 acceptance-criteria check from the spec; paste command + output into the appendix. Any failure → fix in the relevant page, re-run, re-commit.
- [ ] **Step 2:** Re-read each rebuilt page's visible copy against the §18 ten questions; record pass; rework any section that reads as a synonym-swap of the original.
- [ ] **Step 3:** `git log --oneline` since branch point — confirm one reviewable commit per task.
- [ ] **Step 4:** Summarise open `[FACT REQUIRED]` markers into a single checklist section at the end of the audit doc for the business owner.
- [ ] **Step 5: Commit** `git commit -m "Add verification log + consolidated FACT REQUIRED checklist"`

**Verification:** all §6 checks green in the appendix; §18 pass recorded for every page; `[FACT REQUIRED]` checklist complete.

---

## Self-Review

**Spec coverage:** §1–18 of the master prompt → Tasks 2–4 (+5 publish). HTML rebuild scope table in spec §4 → Tasks 6–13. Contamination purge (spec §1) → Tasks 1, 6–13. Verifiability/claims rule (spec §D4/§5) → Tasks 3, 8, 10, 13, 14. `toilet-renovatie` (D7) → Task 11. robots/sitemap (spec §6.7) → Task 13. Acceptance criteria (spec §6) → Task 14. No neighbourhood pages (D6) → Task 4 §9 + Task 11 Step 4. Legal pages (spec §4) → Task 12. No gap found.

**Placeholder scan:** `[FACT REQUIRED …]` markers are intentional deliverable content, not plan placeholders. No "TBD/TODO/handle edge cases" left. Code steps (JSON-LD validation, greps, sitemap) show exact commands.

**Type consistency:** page IDs `P1`–`P8` defined in Task 2 §5, consumed in Tasks 3, 6–12. Canonical host string, `@id` value, `lang="nl-BE"`, phone `+32491980272`, hours `Mo-Su 08:00-17:00` used identically across tasks. Verification "trio" = `file` + contamination grep + JSON-LD parse, defined in Task 6 Step 7, referenced by name after.
