# Badkamer Renovatie Antwerpen — Complete Audit & Original Rebuild

**Prepared:** 2026-08-31
**Site audited:** `https://badkamerrenovatie.montegava.com/` (static mirror in this repository)
**Scope:** Full strategic audit + first-principles rebuild of all real pages
**Published version (interactive):** _Artifact URL added in section header after publication_

> **Method note.** This document treats the current site as a *dataset about a
> business*, not as a template to preserve. Every rebuilt page below was
> reconstructed from the underlying facts, the customer, and the search intent —
> not by rewording the existing copy. Where a fact is needed and cannot be
> verified, it is marked `[FACT REQUIRED FROM BUSINESS OWNER]` with a precise
> description of what is needed and where it goes. Nothing is invented.

---

## 1. Executive Summary

**What this site is.** `badkamerrenovatie.montegava.com` trades as *Badkamer
Renovatie Antwerpen* and sells complete and partial bathroom renovations to
homeowners and apartment owners in Antwerp. It is a WordPress/Elementor site
built by the agency MONTEGAVA and is one node in a network of near-identical
"Badkamer Renovatie \<place\>" microsites (siblings for Deurne, Merksem,
Borgerhout and Berchem are linked in its own footer). The work is delivered by
**Avant Garde Afbouw**, an Amsterdam-based finishing contractor (stucwerk,
schilderwerk, tegelwerk, vloerverwarming).

**The three problems.**

1. **Cross-city template contamination.** The site was cloned from Dutch
   templates and the find/replace was never finished. The contact page's
   structured data still says *"Badkamer Renovatie Amsterdam"*; the FAQ names
   **Nijmegen** commuter towns (Lent, Wijchen, Beuningen, Groesbeek, Arnhem) as
   the service area; the home FAQ lists **Amsterdam** districts (De Pijp,
   IJburg, Zuid/Noord/West/Oost); there is a `/toilet-renovatie-nijmegen/`
   directory — a lorem-ipsum 404 — linked from every footer; image alt text
   reads "badkamer renovatie nijmegen"; and every page declares
   `lang="en-US"`. A visitor or a search engine can see this is a spun template.

2. **Unverifiable trust claims.** "15+ jaar ervaring", "500+ projecten", "5.0 /
   500+ tevreden klanten", "gecertificeerd vakmanschap" and an unspecified
   "garantie" appear throughout. None can be verified from any public source for
   this business or for Avant Garde Afbouw, and the company identity block uses
   a **Dutch KVK number** (67228275) rather than a Belgian enterprise (KBO)
   number. Under Belgian market-practice law (WER Boek VI) and Google's own
   quality guidance, unsubstantiated superlatives and review claims are a
   liability, not an asset.

3. **Thin, duplicated, template-shaped content.** The home page and `/faq`
   repeat FAQ answers almost verbatim; `/diensten` repeats the home page's
   three-service block; the "4 steps" and "3 services" structures are the
   template's, not this business's; and there is no genuinely Antwerp-specific
   information anywhere (permits, VME/syndicus rules, the 6% renovation-VAT
   rule, access and parking for works in the city, the housing stock).

**Recommended path.** Keep the site small (it does not need dozens of pages),
but make every page genuinely original and locally useful, remove all
contamination, fix the technical defects, and either **substantiate or remove**
every trust claim. This document delivers the strategy plus rebuilt, ready-to-
paste Dutch content for all seven real pages and one new page
(`/toilet-renovatie-antwerpen/`).

**Expected outcome.** A small, honest, locally relevant site that can rank on
its own merits for "badkamer renoveren Antwerpen" and related intents, converts
better because it answers real pre-purchase questions, and carries no legal or
reputational exposure from invented claims.

---

## 2. Current Website Risk Assessment

| # | Risk | Severity | Why it matters | Who it hurts |
|---|------|----------|----------------|--------------|
| R1 | **Visible cross-city contamination** (Amsterdam in schema, Nijmegen towns in FAQ, Amsterdam districts in FAQ, "nijmegen" alt text, `/toilet-renovatie-nijmegen/`) | Critical | Signals a spun template to users and Google; destroys local trust; the FAQ actively misstates the service area | Conversion, brand credibility, local ranking |
| R2 | **Unverifiable claims** ("15+ jaar", "500+", "5.0", "gecertificeerd", "garantie" with no term) | Critical | WER Boek VI (misleading commercial practices) exposure in Belgium; erodes E-E-A-T; a single challenged claim discredits the rest | Legal exposure, trust, conversion |
| R3 | **Wrong legal identity** — Dutch KVK number, Amsterdam operator, no Belgian KBO/BTW-BE, possibly non-real Antwerp address | Critical | A Belgian consumer cannot verify who they are contracting with; invoicing/VAT (6% vs 21%) and warranty claims depend on the real entity | Legal, trust, conversion |
| R4 | **Network duplicate content** — sibling microsites (Deurne, Merksem, Borgerhout, Berchem) on the same template, cross-linked in the footer | High | Google may treat the cluster as doorway pages; the footer sends the visitor to competitors-in-network | Ranking of the whole cluster |
| R5 | **Lorem-ipsum page indexed path, linked sitewide** — `/toilet-renovatie-nijmegen/` is a `noindex` 404 with "Fusce non tortor…" but every footer links to it as "Toilet renovatie" | High | Broken internal link on every page; wastes a high-intent query slot; looks abandoned | UX, crawl signals, conversion |
| R6 | **Technical SEO defects** — relative `rel=canonical` (`index.html`), `lang="en-US"`, `inLanguage:"en-US"`, multiple `<h1>` on `/diensten` and `/faq`, no `robots.txt`, no `sitemap.xml` | High | Canonical ambiguity, wrong language targeting, weak heading semantics, no crawl guidance | Indexing, ranking |
| R7 | **Thin & duplicated copy** — home ↔ `/faq` FAQ overlap, home ↔ `/diensten` service block, generic "dream bathroom" filler | Medium | Little unique value per URL; keyword cannibalization between home and `/faq` | Ranking, engagement |
| R8 | **Broken characters** — UTF-8 mojibake ("efficiÃ«nt", "âœ“", "�") in visible text on several pages | Medium | Looks unmaintained; small but compounding trust hit | Brand perception |
| R9 | **Weak/absent structured data integrity** — `Organization` name differs by page (Antwerpen vs Amsterdam); `aggregateRating` implied by "5.0" but not in schema (or if added, unverifiable) | Medium | Inconsistent entity graph; rating rich-result risk if claimed without a real review source | Rich results eligibility, trust |
| R10 | **No conversion instrumentation visible** — single contact form, no phone-click tracking, no distinct thank-you URL | Low/Med | Cannot measure which pages drive leads; hard to improve | Optimisation capacity |

---

## 3. Complete Page Inventory

**Summary table**

| ID | URL | Type | Current `<title>` | `<h1>` | Robots | Intent | Primary keyword (current) | Main CTA | Approx. words | Key issues |
|----|-----|------|-------------------|--------|--------|--------|---------------------------|----------|--------------|------------|
| P1 | `/` | Home / commercial-local | Badkamer Renovatie Antwerpen\| Vrijblijvende Inspectie & Offerte | ✅ 1 | index,follow | Local + commercial | badkamer renovatie Antwerpen | "Vrijblijvende Inspectie" → `/contact/` | ~1,200 | FAQ contamination (Amsterdam districts), concat tokens, unverifiable claims, template 4-step/3-service, FAQ dup with P4 |
| P2 | `/diensten/` | Service overview | Diensten - Badkamer Renovatie Antwerpen | ❌ 2 | index,follow | Commercial investigation | badkamer renovatie diensten | "Vrijblijvende Inspectie" | ~450 | 2× `<h1>`; service text duplicates P1; img alt "nijmegen" ×2; JSON-LD caption "nijmegen"; very thin |
| P3 | `/over-ons/` | Trust / about | Over Ons - Badkamer Renovatie Antwerpen | ✅ 1 (+H5 eyebrow) | index,follow | Commercial investigation / trust | over ons badkamer renovatie | "Vrijblijvende Inspectie" | ~400 | "0+ jaar" counter, "500+ Renovaties", generic story, no team, no real proof |
| P4 | `/faq/` | Informational | FAQ - Badkamer Renovatie Antwerpen | ❌ 2 | index,follow | Informational (pre-purchase) | badkamer renovatie vragen Antwerpen | "Vrijblijvende Inspectie" | ~600 | 2× `<h1>`; service-area answer = Nijmegen towns; overlaps P1 FAQ; no Antwerp-specific Q's |
| P5 | `/contact/` | Conversion | Contact - Badkamer Renovatie Antwerpen | ✅ 1 | index,follow | Transactional / local | contact badkamer renovatie Antwerpen | Contact form | ~150 | **Schema says "Amsterdam"** ×4; English form labels; KVK (NL) number; mojibake; no map, no route info |
| P6 | `/toilet-renovatie-nijmegen/` | (currently 404) | Page not found - Badkamer Renovatie Antwerpen | "404" | noindex,follow | — | — | "Back To Home" | ~40 (lorem) | Lorem ipsum; linked sitewide as "Toilet renovatie"; wrong-city slug → rebuild as P6′ `/toilet-renovatie-antwerpen/` |
| P7 | `/privacy-policy/` | Legal | privacy policy - Badkamer Renovatie Antwerpen | ✅ 1 | noindex,follow | — | — | — | ~450 | Names a third entity ("Badkamer Renovatie Centrum"); `[01-01-2024]` placeholder; not Belgian-law specific; lowercase title |
| P8 | `/algemene-voorwaarden/` | Legal | Algemene Voorwaarden - Badkamer Renovatie Antwerpen | ✅ 1 | (verify) | — | — | — | ~?? | Generic template T&Cs; entity-name inconsistency; NL tone; not verified against Belgian consumer law |

**Per-page detail**

### P1 — Home `/`
- **Meta description:** "Transformeer uw badkamer met Badkamer Renovatie Antwerpen✓ Volledig op maat ✓ Vakmanschap ✓ 15+ jaar ervaring ✓ Vrijblijvende Inspectie & Offerte"
- **Canonical:** `index.html` (relative — defect)
- **H2/H3 outline (current):** H2 "…uitgevoerd met oog voor detail" · H2 "Maatwerk oplossingen voor elke badkamer" · H2 "…afgestemd op jouw woning" · H2 "Recente Projecten" (H3 ×6 project titles) · H2 "De 4 stappen van badkamer renovatie" (H3 1–4) · H2 "Uw partner voor badkamer renovatie" (H3 Complete/Deel/Ontwerp) · H2 "Wat klanten over ons zeggen" · H2 "Veelgestelde vragen" (H5 ×8) · H2 "Een badkamer renovatie die past bij de woning" (H3 ×4) · H2 "Plan jouw gratis badkamer inspectie"
- **Schema:** `WebPage`, `ImageObject`, `BreadcrumbList`, `WebSite`, `Organization`, plus a separate `FAQPage` (8 Q). `inLanguage` "en-US".
- **Secondary keywords:** badkamer verbouwen Antwerpen, badkamer renoveren, inloopdouche, maatwerk badkamer, badkamerspecialist
- **Internal links:** nav (×2), "Vrijblijvende Inspectie" → `/contact/`, footer menu, `/toilet-renovatie-nijmegen/`, legal pages
- **External links:** 5 sibling montegava subdomains, montegava.com
- **Conversion purpose:** book a "vrijblijvende inspectie" via `/contact/`
- **Informational purpose:** explain what a full renovation covers; reassure on process
- **Duplicate/thin:** FAQ block near-duplicates P4; "Maatwerk oplossingen…" and "…afgestemd op jouw woning" H2s say the same thing twice
- **Cannibalisation:** competes with P4 for "badkamer renovatie Antwerpen kosten/duur/garantie"
- **Copied/similar:** 4-step process and 3-service triad are template skeletons; "Transformeer uw badkamer" / "badkamerdromen" filler
- **Trust issues:** every headline number unverifiable; testimonials show as a heading with no attributable content extracted
- **Missing:** price framing, permits/VAT, VME context, real projects with location/date, who does the work
- **UX issues:** three consecutive near-identical intro H2 sections before any substance; concat tokens ("Antwerpenuitgevoerd")

### P2 — Diensten `/diensten/`
- **Meta/OG description:** long run-on beginning "Onze diensten Specialist in moderne badkamerrenovaties…"
- **Outline:** H1 "Diensten" + H1 "Onze diensten" (bug) · H2 "Ontdek Onze Diensten." · H3 Complete / Deel / Ontwerp (×2 sets — card + section) · H3 "Plan jouw gratis badkamer inspectie in Antwerpen"
- **Schema:** `WebPage`, `ImageObject` (caption "badkamer renovatie nijmegen"), `BreadcrumbList`, `WebSite`, `Organization`
- **Issues:** ~450 words for the money page; text is the home block verbatim; `alt="badkamer renovatie nijmegen"` (l.353), `alt="badkamer verbouwen nijmegen"` (l.405)
- **Missing:** what each service actually includes, sequence, what the client decides, price drivers, examples

### P3 — Over ons `/over-ons/`
- **Outline:** H1 "Over ons" · H5 eyebrow "badkamer renovatie Antwerpen" · H3 "Over Ons" · H3 Persoonlijke Aanpak / 500+ Renovaties / Hoogwaardige Afwerking · H3 "Persoonlijke aanpak met vakmanschap centraal" · H3 CTA
- **Content:** two generic paragraphs about "comfort, rust en uitstraling"; a "0+ jaar Ervaring" animated counter; "honderden badkamers … in Antwerpen en omgeving"
- **Missing:** the real story (Avant Garde Afbouw, why Antwerp, since when), named people, qualifications, insurance, warranty terms, real project photos

### P4 — FAQ `/faq/`
- **Outline:** H1 "FAQ" + H1 "Veelgestelde vragen" (bug) · H5 ×8 questions · H3 CTA
- **Questions (current):** duur (1–3 weken) · kosten · "Werken jullie alleen in Antwerpen?" → **Lent, Wijchen, Beuningen, Groesbeek, Arnhem** · gratis inspectie · badkamer+toilet samen · toilet renovatie · garantie · hoe snel starten
- **Schema:** `FAQPage` mirrors the above, including the Nijmegen answer
- **Issues:** 2× `<h1>`; answers overlap P1; the "…tegelijk renoveren" answer is byte-identical to P1's; no Antwerp-specific question (permits, VME, VAT, access)

### P5 — Contact `/contact/`
- **Outline:** H1 "Vrijblijvende inspectie" · H4 "Plan jouw gratis badkamer inspectie" · H5 "contacteer ons" · H3 "Neem contact op?"
- **Schema (l.22):** `WebPage` name "Contact - Badkamer Renovatie **Amsterdam**"; `WebSite` name "Badkamer Renovatie **Amsterdam**"; `Organization` name "Badkamer Renovatie **Amsterdam**"; logo caption "…Amsterdam"; `inLanguage` "en-US"
- **NAP shown:** Van Lissumstraat 45, 2100 Antwerpen · +32491980272 · KVK-nummer 67228275
- **Form:** labels "Name / Phone / Email / Message" (English); button "Versturen"
- **Missing:** map, route/parking note, response-time expectation, real entity + KBO/BTW-BE, alternative contact (WhatsApp/phone hours)

### P6 — `/toilet-renovatie-nijmegen/` (to be replaced)
- 404 template, `noindex,follow`, body is lorem ipsum, H1 "404", link "Back To Home"
- Linked as "Toilet renovatie" from the footer of **all 8 pages**
- **Action:** build `/toilet-renovatie-antwerpen/` (P6′), repoint all footers, `git rm` the Nijmegen dir, document a 301

### P7 — Privacy `/privacy-policy/`
- Title lowercase "privacy policy"; body header "Privacyvoorwaarden voor **Badkamer Renovatie Centrum**"; 8 numbered clauses; "Laatst bijgewerkt op **[01-01-2024]**"; `noindex,follow`
- Generic GDPR-flavoured text, no controller identity, no DPO/contact, no cookie specifics, no Belgian references

### P8 — Algemene voorwaarden `/algemene-voorwaarden/`
- Generic Dutch T&Cs template; entity naming inconsistent with the rest of the site; not verified against Belgian consumer law (WER Boek VI, 2-year conformity, herroepingsrecht scope for works contracts)

---

## 4. Content Similarity Assessment

Classification per the brief: **A** keep (generic, naturally belongs to the
topic) · **B** rebuild (useful topic, wording/structure must be independent) ·
**C** remove (no meaningful value / unnecessary template dependency) · **D**
replace with real business information.

| Page | Section | Class | Reason |
|------|---------|-------|--------|
| P1 | Hero ("Badkamer Renovatie Antwerpen" + "Volledig Op Maat / Vrijblijvende Inspectie / Gecertificeerd Vakmanschap") | **B / D** | Keep a hero, but "Gecertificeerd Vakmanschap" is an unverified claim (D → prove or drop); rewrite headline/subhead from scratch |
| P1 | "…uitgevoerd met oog voor detail" + "Maatwerk oplossingen…" + "…afgestemd op jouw woning" (3 near-identical intro blocks) | **C** (merge to one) | Three sections saying the same thing; collapse into one substantive "what a full renovation covers" block |
| P1 | "Recente Projecten" (6 tiles) | **D** | Only valuable with real photos + location + date + scope; otherwise remove |
| P1 | "De 4 stappen van badkamer renovatie" | **B** | Process transparency is good; the 4-step wording/structure is the template's — rebuild as this firm's actual sequence |
| P1 | "Uw partner…" 3-service triad | **B** | Overlaps P2 verbatim; keep a short services teaser, rewrite, link to P2 |
| P1 | "Wat klanten over ons zeggen" | **D** | Needs real, attributable reviews with source; otherwise remove the section |
| P1 | "Veelgestelde vragen" (8 Q) | **B / C** | Cut to 3–4 home-level Q with fresh wording; move depth to P4; remove Amsterdam-district answer (contamination) |
| P1 | "Een badkamer renovatie die past bij de woning" (oudere woningen / compacte badkamers / appartementen & VvE / indeling) | **B / D** | Best idea on the page; rebuild with real Antwerp specifics (rijhuizen, herenhuizen, VME/syndicus, betonvloeren, gietijzeren afvoer) — "VvE" is the Dutch term, must become "VME/syndicus" |
| P1 | Footer tagline "Meer dan 15 jaar … 500+ projecten" | **D** | Unverifiable — replace with claim-safe wording or a filled `[FACT REQUIRED]` |
| P2 | 3-service cards + 3-service sections (duplicate of each other and of P1) | **B** | Rebuild as one set of substantive service explanations; deduplicate |
| P2 | "Plan jouw gratis badkamer inspectie in Antwerpen" | **A** | Generic CTA section — fine to keep, light rewrite |
| P3 | "Bij Badkamer Renovatie Antwerpen geloven wij dat een badkamer meer moet zijn dan…" | **C** | Pure filler opening |
| P3 | "Door de jaren heen … honderden badkamers … in Antwerpen en omgeving" | **D** | Replace with the real story + `[FACT REQUIRED]` counts/dates |
| P3 | "0+ jaar Ervaring" counter, "500+ Renovaties" | **D** | Unverifiable metrics |
| P3 | "Persoonlijke aanpak met vakmanschap centraal" | **B** | Reasonable point, template wording — rebuild and add substance (who, qualifications) |
| P4 | duur / kosten / garantie / toilet / badkamer+toilet | **B** | Keep the topics, rewrite answers with Antwerp specifics and no claim overlap with P1 |
| P4 | "Werken jullie alleen in Antwerpen?" → Nijmegen towns | **D** | Contamination — replace with the real Antwerp service area |
| P4 | "…badkamer en toilet tegelijk…" (identical to P1) | **C** on P1 / **B** on P4 | De-duplicate: keep on P4, rewrite; drop from P1 |
| P5 | Contact intro / "Neem contact op?" | **B** | Rewrite; add response-time + what-happens-next |
| P5 | `Organization`/`WebSite` schema "Amsterdam" | **D** | Replace with the real Antwerp entity |
| P5 | English form labels | **C** | Replace with Dutch |
| P6 | entire page (lorem ipsum) | **D** | Build a real `/toilet-renovatie-antwerpen/` page |
| P7/P8 | legal text | **B** (+ lawyer) | Fix entity name + `lang` + contamination now; flag for legal review against Belgian law |
| all | footer "Werkgebied" links to sibling microsites | **C** | Remove outbound links to network competitors; replace with plain-text Antwerp districts |
| all | `lang="en-US"`, `og:locale=en_US`, `inLanguage:"en-US"` | **D** | → `nl-BE` / `nl_BE` |
| all | "Antwerpen\<woord\>" concatenations | **C** | Find/replace artefact — fix every instance |

---

## 5. New Information Architecture

**Principle.** This is a single-location service business with one core offer
(bathroom renovation) and one adjacent offer (toilet renovation). It needs a
*small* site where every page earns its place. No neighbourhood/doorway pages
are created here (the sibling microsites already occupy those slugs — see §9);
instead a single honest "Werkgebied" block covers the districts.

**Main navigation:** Home · Diensten · Toilet renovatie · Over ons ·
Veelgestelde vragen · Contact
(secondary/footer: Privacybeleid · Algemene voorwaarden)

**Page set & IDs**

| ID | Page | URL slug | Exists? | Intent | Why it exists / who it serves | Conversion goal | How it differs from the others | Internal-linking role |
|----|------|----------|---------|--------|-------------------------------|-----------------|------------------------------|-----------------------|
| **P1** | Home | `/` | rebuild | Local + commercial ("badkamer renoveren Antwerpen") | The homeowner comparing local renovators; needs to grasp scope, process, who does it, and the local fit in 30 seconds | Book a plaatsbezoek (→ P5) | Broadest; overview + local-fit + trust; sends depth to P2/P4/P6 | Hub. Links out to every page; receives links from all |
| **P2** | Diensten | `/diensten/` | rebuild | Commercial investigation | Someone deciding *what* they need — full vs partial vs design-only | Request an offerte / plaatsbezoek | Explains scope, sequence, decisions, price drivers per service — no local-fit or company story | Linked from P1 services teaser; links to P6 and P4 |
| **P6** | Toilet renovatie Antwerpen | `/toilet-renovatie-antwerpen/` | **new** (replaces P6) | Commercial + local ("toilet renoveren Antwerpen") | The narrower, common job — separate toilet room; often searched on its own | Request an offerte / plaatsbezoek | Single-room scope, small-space solutions, combine-with-bathroom logic; not the full-renovation page | Linked from P1, P2, P4 nav/footer; links back to P2 |
| **P3** | Over ons | `/over-ons/` | rebuild | Trust / commercial investigation | The visitor asking "who are these people, can I trust them with my home and my money" | Build confidence → P5 | The only page about the *company* (operator, people, qualifications, guarantees, insurance) | Linked from P1 trust block and P5; links to P5 |
| **P4** | Veelgestelde vragen | `/faq/` | rebuild | Informational (pre-purchase) | The visitor with specific blockers: cost drivers, duration, permits, VME, VAT, living through the works | Remove objections → P5 | Depth Q&A; no marketing prose; the only page covering permits/VME/VAT | Linked from P1 (mini-FAQ "meer vragen"), P2, P6; links to P5, P2, P6 |
| **P5** | Contact | `/contact/` | rebuild | Transactional / local | Ready to act — wants to reach the business and know what happens next | Submit the form / call | Only page with NAP, map, route/parking, response-time, entity identity | Destination of every primary CTA |
| **P7** | Privacybeleid | `/privacy-policy/` | light pass + legal review | — | Compliance | — | — | Footer only; `noindex` |
| **P8** | Algemene voorwaarden | `/algemene-voorwaarden/` | light pass + legal review | — | Compliance | — | — | Footer only |

**Decision D8 resolved — one `/diensten` page, not a split.** The three offers
(complete renovation, partial renovation/upgrades, design & advice) share most
of their substance and the business has limited verifiable unique content per
offer. Splitting into `/complete-badkamerrenovatie/`, `/deelrenovatie/`,
`/badkamerontwerp/` would create three thin pages competing with each other and
with P1. Instead: **one strong `/diensten/` page with a clear anchored section
per offer.** `/toilet-renovatie-antwerpen/` *is* kept separate because "toilet
renoveren" is a distinct high-intent query, the slug is already wired sitewide,
and the single-room scope genuinely differs. Future dedicated pages
(`/inloopdouche-plaatsen-antwerpen/`, `/badkamer-renovatie-appartement-antwerpen/`)
are listed as content-gap opportunities in §14, to be built only when there is
real project material to support them.

**Removed from the IA:** the "Recente Projecten" tiles and the testimonials
carousel become *components* that appear only once real, attributable material
exists; the sibling-microsite footer links; the `/toilet-renovatie-nijmegen/`
path.

---

## 6. Keyword & Search Intent Map

Belgian/Flemish phrasing throughout ("renoveren" and "verbouwen" both used
locally; "badkamerrenovatie" one word is common; VAT known as "btw", the
reduced rate as "6% btw"). No keyword is targeted by more than one page.

| Page | Primary keyword | Secondary keywords | Semantic entities to cover | Intent | Geo modifiers | Related questions (People-Also-Ask style) |
|------|-----------------|--------------------|-----------------------------|--------|---------------|-------------------------------------------|
| **P1** Home | badkamer renoveren Antwerpen | badkamerrenovatie Antwerpen, badkamer verbouwen Antwerpen, badkamer laten renoveren, badkamerspecialist Antwerpen | sloopwerk, leidingwerk, waterdichting, tegelwerk, sanitair, inloopdouche, ventilatie, vloerverwarming, afwerking, rijhuis, herenhuis, appartement, VME/syndicus | Local + commercial | Antwerpen, (districten: Deurne, Berchem, Borgerhout, Merksem, Wilrijk, Antwerpen-Zuid, Antwerpen-Noord) | Wat kost een badkamerrenovatie in Antwerpen? Hoe lang duurt het? Heb ik een vergunning nodig? |
| **P2** Diensten | badkamerrenovatie diensten Antwerpen | complete badkamerrenovatie, badkamer deelrenovatie, badkamer upgraden, badkamerontwerp, sanitair vervangen, tegelwerk vernieuwen | volledige renovatie vs deelrenovatie, projectverloop, materiaalkeuze, prijsbepalende factoren, planning, oplevering | Commercial investigation | Antwerpen | Wat valt onder een complete renovatie? Kan ik alleen de douche laten vervangen? |
| **P6** Toilet renovatie | toilet renoveren Antwerpen | toiletrenovatie Antwerpen, wc renoveren, gastentoilet renoveren, inbouwreservoir plaatsen, hangtoilet plaatsen | inbouwreservoir, hangtoilet, fonteintje, tegelwerk klein oppervlak, ventilatie, vloerafwerking, combineren met badkamer | Commercial + local | Antwerpen | Wat kost een toilet renoveren? Kan het samen met de badkamer? Hoe lang duurt een toiletrenovatie? |
| **P3** Over ons | badkamerrenovatie Antwerpen ervaring | wie voert de werken uit, vast team badkamer, Avant Garde Afbouw, gecertificeerd tegelwerk | operator-identiteit, vakmensen, kwalificaties, verzekering, waarborg/garantie, werkwijze, één aanspreekpunt | Trust / commercial investigation | Antwerpen | Wie doet het werk? Zijn jullie verzekerd? Welke garantie geven jullie? |
| **P4** FAQ | badkamerrenovatie Antwerpen vragen | badkamerrenovatie prijs Antwerpen, badkamerrenovatie duur, vergunning badkamer Antwerpen, btw 6% renovatie, badkamer renoveren appartement | prijsdrijvers, doorlooptijd, stedenbouwkundige melding/vergunning, VME-reglement + syndicus, 6% vs 21% btw, asbestattest, bewoonbaarheid tijdens werken, waterdichtingsgarantie | Informational (pre-purchase) | Antwerpen | Heb ik een vergunning nodig? Geldt 6% btw? Mag ik in mijn appartement zomaar renoveren? Kan ik de badkamer gebruiken tijdens de werken? |
| **P5** Contact | badkamerrenovatie Antwerpen contact | offerte badkamer Antwerpen, plaatsbezoek badkamer, afspraak badkamerrenovatie | NAP, bereikbaarheid, responstijd, offertetraject, werfzone/parkeren stad Antwerpen | Transactional / local | Antwerpen | Hoe vraag ik een offerte aan? Hoe snel krijg ik antwoord? |

**Cannibalisation / consolidation calls**
- P1 and P4 currently both target *kosten/duur/garantie*. Resolution: P1 keeps a
  3–4 item mini-FAQ with **home-level** phrasing and a link to P4; P4 owns the
  detailed answers. No overlap in wording.
- P1's three intro H2 sections → merged (one section).
- No `aggregateRating` schema on any page unless a real, cited review source
  exists (§13). "5.0" text claims removed site-wide.

---

## 7. Topical Authority Map

Small and deliberate — enough to be credibly "the bathroom-renovation
specialist for Antwerp", not a content farm.

### Core commercial topics (must own)
| Topic | Intent | Target page | Primary theme | Supporting keywords | Internal links | New page? |
|-------|--------|-------------|---------------|--------------------|----------------|-----------|
| Complete bathroom renovation in Antwerp | Commercial-local | P1 + P2 (section) | End-to-end renovation: scope, process, result | badkamer renoveren/verbouwen Antwerpen, complete badkamerrenovatie | P1↔P2↔P4↔P5 | No |
| Partial renovation / upgrades | Commercial investigation | P2 (section) | When a full strip-out isn't needed | douche vervangen, tegelwerk vernieuwen, sanitair upgraden | P2→P4, P2→P5 | No |
| Toilet renovation in Antwerp | Commercial-local | P6 | Separate WC room, small-space | toilet/wc renoveren Antwerpen, inbouwreservoir | P6↔P2, P6→P4, P6→P5 | **Yes (new)** |

### Supporting (pre-purchase) topics
| Topic | Intent | Target page | Notes | New page? |
|-------|--------|-------------|-------|-----------|
| What a bathroom renovation costs in Antwerp & what drives the price | Informational/commercial | P4 (answer) + P2 (price-drivers block) | Give the *drivers* honestly; give ranges only if `[FACT REQUIRED]` filled | No |
| How long it takes | Informational | P4 | Realistic ranges by scope; no false precision | No |
| Living through the works / using the bathroom during | Informational | P4 | Practical, reassuring, specific | No |
| Choosing materials (tegels, sanitair, verlichting) | Informational | P2 (design & advice section) | Position as guided decisions | Later (guide) |

### Educational / expertise topics (E-E-A-T)
| Topic | Intent | Target page | New page? |
|-------|--------|-------------|-----------|
| Permits & notifications for a bathroom in Antwerp (stedenbouwkundige melding/vergunning; when none is needed) | Informational | P4 (answer), later a dedicated guide | Later |
| Renovating a bathroom in an appartement: VME-reglement, syndicus approval, common pipes/risers | Informational | P4 (answer) + P1 (local-fit block) | Later (guide) |
| 6% vs 21% btw for renovation of a home older than 10 years | Informational | P4 (answer) | No |
| Asbestattest for pre-2001 homes (relevance to strip-out) | Informational | P4 (answer) | No |
| Waterdichting / tanking before tiling — why it matters | Educational | P2 (complete-renovation section) | Later |

### Local topics (genuine, not doorway)
| Topic | Target | Treatment |
|-------|--------|-----------|
| Districts served (Deurne, Berchem, Borgerhout, Merksem, Wilrijk, Antwerpen-Zuid/-Noord, Ekeren, Hoboken) | P1 "Werkgebied" block, P5 | Plain text + one line on access/parking for city works; **no per-district pages** while sibling microsites exist (§9) |
| Antwerp housing stock (arbeiders­rijhuizen, herenhuizen, jaren-'30 gordel, naoorlogse appartementen) and what each means for a bathroom job | P1 local-fit block | Specific, first-hand framing |
| Werfzone & parkeervergunning for works in the city / narrow streets | P4 answer, P5 note | Practical logistics |

### Explicitly NOT creating
- Per-neighbourhood landing pages (doorway risk + sibling-site duplication).
- "Best/number 1 bathroom renovator Antwerp" style pages (unverifiable).
- Separate thin pages per material or per fixture (no supporting project content yet).
