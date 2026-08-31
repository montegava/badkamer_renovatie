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

---

## 8. Page-by-Page Rebuild

All body copy below is **ready-to-paste Belgian Dutch**, written from the
business facts and the search intent — not reworded from the current site.
Register: consistent **"u"**. Markers `[FACT REQUIRED FROM BUSINESS OWNER: …]`
name a fact to insert and where; the surrounding copy is written to read
correctly if the marker is simply deleted (i.e. no claim is load-bearing).

### Conventions applied on every page
- `<html lang="nl-BE">`, `<meta property="og:locale" content="nl_BE">`
- `<link rel="canonical" href="https://badkamerrenovatie.montegava.com/<slug>/">` (absolute; home = bare domain)
- Exactly one `<h1>`; `<h2>` for sections, `<h3>` for sub-points; no `<h5>` eyebrows carrying heading weight
- One consistent `Organization` node, `@id` `https://badkamerrenovatie.montegava.com/#organization`, `name` "Badkamer Renovatie Antwerpen", `inLanguage` `nl-BE`
- No "5.0", "500+", "15+ jaar", "gecertificeerd", "beste/nummer 1" unless a `[FACT REQUIRED]` marker is filled with a citable source
- NAP used verbatim wherever it appears:
  - **Badkamer Renovatie Antwerpen** — onderdeel van Avant Garde Afbouw
  - `[FACT REQUIRED FROM BUSINESS OWNER: bevestig het vestigings-/correspondentieadres in Antwerpen. De site vermeldt nu "Van Lissumstraat 45, 2100 Antwerpen" (Deurne) — bevestig of dit een echt kantoor-/werkadres is, anders vervangen door een correct adres of weglaten.]`
  - Tel. +32 491 98 02 72 · e-mail info@badkamerrenovatie.montegava.com
  - Openingsuren: maandag–zaterdag, 8.00–17.00 `[FACT REQUIRED: bevestig openingsuren; de site zegt nu ma–zo 8–17 u]`
  - `[FACT REQUIRED FROM BUSINESS OWNER: Belgisch ondernemingsnummer (KBO) en btw-BE-nummer. Het huidige "KVK-nummer 67228275" is Nederlands en hoort niet op een Belgische site.]`

---

### PAGE P1 — Home (`/`)

#### A. Page strategy
- **URL:** `/`
- **Page type:** Home / commercial-local landing
- **Primary search intent:** local + commercial — "badkamer renoveren Antwerpen"
- **Target audience:** owner-occupiers (and some landlords) in Antwerp city and
  its districts, planning a full or near-full bathroom renovation in the next
  1–6 months; comparing two or three local firms.
- **Primary topic:** having your bathroom renovated end-to-end by one Antwerp team
- **Primary keyword:** badkamer renoveren Antwerpen
- **Secondary topics:** wat een complete renovatie omvat; hoe het project verloopt; wie de werken uitvoert; hoe de aanpak past bij Antwerpse woningen; eerste kostenindicatie
- **Conversion goal:** book a free plaatsbezoek via P5 (form or phone)
- **Unique value proposition:** één vast team dat de hele badkamer doet — van
  uitbraak en leidingwerk tot waterdichting, tegelwerk en afwerking — met één
  aanspreekpunt en een planning die vooraf vastligt, afgestemd op het type
  Antwerpse woning (rijhuis, herenhuis, appartement).
- **Differentiation strategy:** concrete scope-of-works and a real project
  sequence instead of "droombadkamer" language; genuine local fit (housing
  stock, VME/syndicus, access) instead of a district keyword list; claim-safe
  trust (how the work is organised) instead of unverifiable numbers.

#### B. Recommended structure
1. `<h1>` **Badkamer renoveren in Antwerpen** + one-line subhead + primary CTA
2. `<h2>` **Wat een complete badkamerrenovatie bij ons omvat** — scope list (replaces the three duplicate intro blocks)
3. `<h2>` **Zo verloopt uw renovatie** — the real sequence (replaces the template "4 stappen")
4. `<h2>` **Afgestemd op uw type woning in Antwerpen** — local-fit block: rijhuis/herenhuis · appartement + VME/syndicus · naoorlogse bouw · compacte badkamer (replaces "past bij de woning")
5. `<h2>` **Onze diensten in het kort** — 3-line teaser → P2 and → P6
6. `<h2>` **Veelgestelde vragen** — 4 home-level Q&A + link to P4
7. `<h2>` **Een plaatsbezoek aanvragen** — CTA section → P5
8. (Optional, only if real: `<h2>` **Recente projecten** / **Wat klanten zeggen** — otherwise omitted)

#### C. SEO elements
- **SEO title:** `Badkamer renoveren in Antwerpen | Badkamer Renovatie Antwerpen` (58)
- **Meta description:** `Uw badkamer volledig laten renoveren in Antwerpen door één vast team: uitbraak, leidingwerk, waterdichting, tegelwerk, sanitair en afwerking. Vraag een gratis plaatsbezoek aan.` (169 → trim to: `Uw badkamer volledig laten renoveren in Antwerpen door één vast team: van leidingwerk en waterdichting tot tegelwerk en afwerking. Vraag een gratis plaatsbezoek aan.` (156))
- **H1:** Badkamer renoveren in Antwerpen
- **URL slug:** `/`
- **Canonical:** `https://badkamerrenovatie.montegava.com/`
- **Robots:** `index, follow`
- **OG title:** Badkamer renoveren in Antwerpen
- **OG description:** Eén vast team voor uw volledige badkamerrenovatie in Antwerpen. Vraag een gratis plaatsbezoek aan.

#### D. Full original content (Dutch, ready to paste)

**H1: Badkamer renoveren in Antwerpen**

Subhead: Eén vast team voor de volledige renovatie van uw badkamer — van uitbraak tot afwerking, met één aanspreekpunt en een planning die vooraf vastligt.

[Primaire knop: **Gratis plaatsbezoek aanvragen** → /contact/] · [Secundaire link: Bekijk onze diensten → /diensten/]

---

**H2: Wat een complete badkamerrenovatie bij ons omvat**

Een volledige badkamerrenovatie is meer dan nieuwe tegels. Bij een complete renovatie nemen wij het hele traject voor onze rekening:

- **Uitbraak en afvoer** van de bestaande badkamer, inclusief het afvoeren van puin.
- **Leidingwerk**: nieuwe aan- en afvoerleidingen voor water, aanpassingen aan de riolering waar nodig, en een controle van de bestaande afvoer (in oudere Antwerpse woningen vaak nog gietijzer).
- **Elektriciteit**: extra stopcontacten, verlichting en aansluitingen voor spiegelverwarming of een handdoekradiator, uitgevoerd volgens het AREI. Een keuring van de nieuwe kring hoort daarbij `[FACT REQUIRED FROM BUSINESS OWNER: bevestig of u de AREI-keuring zelf regelt of laat uitvoeren door een erkend keuringsorganisme]`.
- **Chape en waterdichting**: een nieuwe chape waar nodig, en een volwaardige waterdichting (tanking) van douchezone en vloer vóór het tegelen. Dit is de stap die later lekken voorkomt.
- **Tegelwerk**: vloer- en muurtegels, inloopdouche met de juiste afschot, plaatsing van profielen en voegwerk.
- **Sanitair en meubel**: toilet of hangtoilet met inbouwreservoir, wastafel en wastafelmeubel, douche- of badkraan, regendouche, radiator.
- **Ventilatie**: mechanische afzuiging of aansluiting op het bestaande systeem, afgestemd op de ruimte.
- **Afwerking**: plafond, schilderwerk, deur en plinten, en een nette oplevering met opkuis.

Wat u kiest — tegels, sanitair, meubel, kleuren — bespreken we samen. Wat technisch nodig is, brengen we vooraf in kaart tijdens het plaatsbezoek, zodat de offerte volledig is en er achteraf geen posten bijkomen die we hadden kunnen zien.

---

**H2: Zo verloopt uw renovatie**

**H3: 1. Plaatsbezoek en opmeting**
We komen langs, meten de ruimte op, controleren leidingen, afvoer en ondergrond, en bespreken wat u wilt. U hoort meteen wat kan, wat aandacht vraagt en welke keuzes de prijs bepalen.

**H3: 2. Offerte en materiaalkeuze**
U krijgt een gedetailleerde offerte per post (uitbraak, techniek, tegelwerk, sanitair, afwerking apart benoemd). Parallel kiest u de materialen; we geven advies over wat past bij de ruimte, het gebruik en het budget.

**H3: 3. Planning**
Na akkoord leggen we een startdatum en een dagenplanning vast. U weet vooraf welke dagen welke ploeg aanwezig is en wanneer de badkamer buiten gebruik is.

**H3: 4. Uitvoering door één ploeg**
Dezelfde vakmensen doen uitbraak, techniek, tegelwerk en afwerking. Eén aanspreekpunt tijdens de hele werf; geen losse onderaannemers die naar elkaar verwijzen.

**H3: 5. Oplevering**
We overlopen het resultaat samen, stellen de laatste punten bij en ruimen op. U krijgt de nodige documenten `[FACT REQUIRED FROM BUSINESS OWNER: welke documenten levert u op — AREI-keuringsverslag, garantiebewijs, onderhoudsadvies? En welke waarborgtermijn geeft u schriftelijk op de uitgevoerde werken?]`.

---

**H2: Afgestemd op uw type woning in Antwerpen**

Antwerpse woningen verschillen sterk, en dat bepaalt mee hoe een badkamer wordt aangepakt.

**H3: Rij- en herenhuizen**
In de 19e- en vroeg-20e-eeuwse gordel (Zurenborg, Zuid, Borgerhout intra muros, Deurne-Noord) zit de badkamer vaak op de eerste verdieping of in een achterbouw. Houten roostering, oude afvoer in gietijzer en beperkte plafondhoogte in de aanbouw vragen om controle vooraf. We kijken naar draagkracht, afschot en de haalbaarheid van een inloopdouche op die plek.

**H3: Appartementen — VME en syndicus**
In een appartementsgebouw lopen de standleidingen door meerdere woningen. Ingrepen aan gemeenschappelijke leidingen, of aan de vloeropbouw boven een buur, vallen onder het reglement van de VME. Vraag tijdig schriftelijke toestemming aan de syndicus; wij leveren op verzoek een korte technische omschrijving die u daarvoor kunt gebruiken. Geluidsisolatie van de vloer en de uren waarop lawaaierige werken zijn toegelaten, stemmen we af op het reglement.

**H3: Naoorlogse bouw**
In appartementen en woningen uit de jaren '60–'80 is de badkamer vaak klein en de leidingaanleg gedateerd. Een deelrenovatie volstaat soms; wanneer de leidingen aan vervanging toe zijn, is een volledige renovatie op termijn voordeliger.

**H3: Compacte badkamers**
Veel stadswoningen hebben een badkamer van 3 tot 5 m². Met een inloopdouche zonder profiel, een hangtoilet en een smaller meubel houdt u loopruimte over. We tekenen vooraf een indeling zodat u ziet wat past.

---

**H2: Onze diensten in het kort**

- **Complete badkamerrenovatie** — het volledige traject, van uitbraak tot oplevering.
- **Deelrenovatie en upgrades** — enkel de douche, het sanitair, het tegelwerk of de verlichting vernieuwen.
- **Toiletrenovatie** — een apart toilet of gastentoilet, los of samen met de badkamer.

[Link: **Bekijk alle diensten** → /diensten/] · [Link: **Toilet renoveren in Antwerpen** → /toilet-renovatie-antwerpen/]

---

**H2: Veelgestelde vragen**

**H3: Wat kost een badkamerrenovatie in Antwerpen?**
De prijs hangt af van de oppervlakte, de staat van de leidingen, de hoeveelheid tegelwerk en uw keuze van sanitair en materialen. Een deelrenovatie kost duidelijk minder dan een volledige renovatie met nieuw leidingwerk en chape. Tijdens het plaatsbezoek overlopen we de prijsbepalende punten en daarna krijgt u een gedetailleerde offerte. Meer detail vindt u op onze [pagina met veelgestelde vragen](/faq/).

**H3: Hoe lang duurt een badkamerrenovatie?**
Een volledige renovatie van een gemiddelde stadsbadkamer neemt doorgaans twee tot drie weken werk op de werf, afhankelijk van droogtijden van chape en waterdichting en van de levertermijn van tegels en sanitair. De juiste planning krijgt u vóór de start.

**H3: Kan ik de badkamer gebruiken tijdens de werken?**
Tijdens een volledige renovatie is de badkamer een aantal dagen niet bruikbaar. Waar mogelijk plannen we zo dat een toilet elders in de woning beschikbaar blijft. Dit bespreken we vooraf.

**H3: Werken jullie in heel Antwerpen?**
Ja. We werken in Antwerpen-stad en de districten Deurne, Berchem, Borgerhout, Merksem, Wilrijk, Ekeren, Hoboken en Antwerpen-Noord en -Zuid. Voor werven in de stad regelen we waar nodig een parkeervergunning voor de werfzone.

[Link: **Alle veelgestelde vragen** → /faq/]

---

**H2: Een plaatsbezoek aanvragen**

Wil u weten wat er mogelijk is voor uw badkamer en wat het ongeveer kost? Vraag een gratis plaatsbezoek aan. We komen langs op een moment dat u past, bekijken de ruimte en bezorgen daarna een offerte op maat. U zit nergens aan vast.

[Primaire knop: **Plaatsbezoek aanvragen** → /contact/] · Of bel [+32 491 98 02 72](tel:+32491980272)

**Footer-tagline (vervangt "Meer dan 15 jaar … 500+ projecten"):**
Badkamer Renovatie Antwerpen — onderdeel van Avant Garde Afbouw. Uw badkamer en toilet volledig gerenoveerd door één vast team, in Antwerpen en omliggende districten. `[FACT REQUIRED FROM BUSINESS OWNER: als u een verifieerbaar aantal afgeronde badkamerprojecten in de regio Antwerpen wil vermelden, geef dat cijfer en het startjaar door; anders blijft deze tekst zonder cijfers.]`

#### E. Conversion optimisation
- **Primary CTA:** "Plaatsbezoek aanvragen" (repeated: hero, after "Zo verloopt uw renovatie", closing section)
- **Secondary CTA:** phone-click `tel:` link; "Bekijk onze diensten"
- **Trust elements (claim-safe):** the scope list, the named sequence, "één ploeg / één aanspreekpunt", operator disclosed (Avant Garde Afbouw), full NAP + KBO once supplied, warranty term once supplied. Add a real project strip / named reviews only when material exists.
- **Objection handling on-page:** cost ("wat bepaalt de prijs"), disruption ("badkamer gebruiken tijdens de werken"), trust ("wie voert de werken uit"), apartment rules (local-fit block).
- **Contact opportunities:** hero, mid-page, footer, sticky header button, phone link.
- **Social proof placement:** directly under the sequence section *if/when* real — 2–3 attributable reviews with first name + district + month/year, or a link to a Google Business Profile.

#### F. Internal linking
- **Out:** → `/diensten/` (anchor "Bekijk onze diensten", "onze diensten"), → `/toilet-renovatie-antwerpen/` ("Toilet renoveren in Antwerpen"), → `/faq/` ("Alle veelgestelde vragen", "pagina met veelgestelde vragen"), → `/over-ons/` ("wie voert de werken uit" in trust context), → `/contact/` (all CTAs, "plaatsbezoek aanvragen")
- **In:** every page's nav + footer; `/over-ons/` and `/faq/` link back to Home as the hub
- **Contextual:** the "Afgestemd op uw type woning" apartment sub-block → `/faq/` anchor on the VME question

#### G. Structured data
- `WebPage` (`@id` `…/#webpage`, `isPartOf` `…/#website`, `inLanguage` `nl-BE`, `about` `…/#organization`)
- `WebSite` (`@id` `…/#website`, `name` "Badkamer Renovatie Antwerpen")
- `Organization` (`@id` `…/#organization`, `name`, `url`, `logo`, `telephone` `+32491980272`, `email`, `areaServed` "Antwerpen", `parentOrganization` { `name`: "Avant Garde Afbouw" }) — **no** `aggregateRating`/`review` unless `[FACT REQUIRED: koppel een echte reviewbron (bv. Google Bedrijfsprofiel-URL) met echte beoordelingen]` is filled
- `BreadcrumbList` (Home)
- `FAQPage` — **only** the 4 questions actually shown on the page, `text` matching the visible answers verbatim
- Consider `LocalBusiness` (subtype `HomeAndConstructionBusiness`) instead of plain `Organization` **once** a real street address + KBO is confirmed; until then keep `Organization` to avoid asserting a `LocalBusiness` address that may not be real.

---

### PAGE P2 — Diensten (`/diensten/`)

#### A. Page strategy
- **URL:** `/diensten/`
- **Page type:** service overview (single page, anchored sections)
- **Primary search intent:** commercial investigation — deciding *what* scope of work is needed
- **Target audience:** homeowner who knows they want work done but not whether they need a full strip-out, a partial refresh, or just design help
- **Primary topic:** the renovation services offered and what each one involves
- **Primary keyword:** badkamerrenovatie diensten Antwerpen
- **Secondary topics:** complete renovatie; deelrenovatie/upgrades; ontwerp & advies; projectverloop; prijsbepalende factoren
- **Conversion goal:** request an offerte / plaatsbezoek
- **UVP:** one team for the whole job, and honesty about when you *don't* need the whole job
- **Differentiation:** each service says what is included, in what order it happens, which decisions are yours, and what moves the price — not three vague paragraphs

#### B. Recommended structure
1. `<h1>` **Onze diensten voor badkamer- en toiletrenovatie in Antwerpen** (single H1 — demote the current second H1)
2. Intro (2 sentences)
3. `<h2 id="complete">` Complete badkamerrenovatie — includes / sequence / your choices / price drivers
4. `<h2 id="deelrenovatie">` Deelrenovatie en upgrades — when it's enough / typical jobs / what to check first
5. `<h2 id="ontwerp">` Badkamerontwerp en advies — what you get / how it feeds the offerte
6. `<h2 id="toilet">` Toiletrenovatie — short teaser → P6
7. `<h2>` Wat de prijs bepaalt — shared price-driver list
8. `<h2>` Offerte aanvragen — CTA → P5

#### C. SEO elements
- **SEO title:** `Diensten: badkamer- & toiletrenovatie in Antwerpen | Badkamer Renovatie Antwerpen` → trim to `Onze diensten voor badkamerrenovatie in Antwerpen | Badkamer Renovatie Antwerpen` (still long; final: `Diensten badkamerrenovatie Antwerpen | Badkamer Renovatie Antwerpen`, 60)
- **Meta description:** `Complete badkamerrenovatie, deelrenovatie of enkel ontwerp en advies in Antwerpen. Ontdek wat elke dienst omvat, hoe de werken verlopen en wat de prijs bepaalt.` (156)
- **H1:** Onze diensten voor badkamer- en toiletrenovatie in Antwerpen
- **URL slug:** `/diensten/`
- **Canonical:** `https://badkamerrenovatie.montegava.com/diensten/`
- **OG title:** Onze diensten voor badkamerrenovatie in Antwerpen
- **OG description:** Wat een complete renovatie, een deelrenovatie en ontwerp & advies precies inhouden — en wat de prijs bepaalt.

#### D. Full original content (Dutch, ready to paste)

**H1: Onze diensten voor badkamer- en toiletrenovatie in Antwerpen**

Wij voeren badkamer- en toiletrenovaties uit met één vast team, van uitbraak tot afwerking. Soms is een volledige renovatie de juiste keuze, soms volstaat het vernieuwen van een deel. Hieronder leest u wat elke dienst inhoudt.

---

**H2: Complete badkamerrenovatie**

Een volledige renovatie waarbij de badkamer tot op de ruwbouw wordt uitgebroken en opnieuw opgebouwd.

**Inbegrepen:** uitbraak en puinafvoer · nieuw aan- en afvoerleidingwerk · elektriciteit volgens het AREI · nieuwe chape waar nodig · waterdichting van douchezone en vloer · vloer- en muurtegels · sanitair, kranen en wastafelmeubel · ventilatie · schilder- en afwerkingswerk · opkuis en oplevering.

**Volgorde van de werken:** uitbraak → leidingwerk en elektriciteit → chape → waterdichting → tegelwerk → plaatsing sanitair → afwerking → oplevering. Tussen chape/waterdichting en tegelwerk zit droogtijd; die staat in de planning.

**Uw keuzes:** indeling, tegels (formaat, kleur, legpatroon), sanitair en kranen, meubel en spiegel, verlichting, type douche (inloop, met deur, regendouche), al dan niet vloerverwarming.

**Wat de prijs bepaalt:** oppervlakte en hoeveelheid tegelwerk · of leidingen en chape vernieuwd worden · verplaatsen van toilet of afvoer · keuze van tegels en sanitair (basis of hoogsegment) · vloerverwarming · maatwerk meubel · bereikbaarheid van de woning.

---

**H2: Deelrenovatie en upgrades**

Niet elke badkamer moet volledig eruit. Een deelrenovatie vernieuwt gericht één of enkele onderdelen.

**Typische opdrachten:** het bad vervangen door een inloopdouche · enkel het sanitair en de kranen vernieuwen · nieuw tegelwerk op een bestaande, gezonde ondergrond · verlichting en stopcontacten bijplaatsen · een nieuw wastafelmeubel en spiegel.

**Wat we eerst controleren:** de staat van de waterdichting en de voegen, de ouderdom van de leidingen en de afvoer, en of de bestaande tegels en ondergrond stabiel genoeg zijn om op verder te werken. Als de leidingen op korte termijn toch vervangen moeten worden, zeggen we dat vooraf — dan is een volledige renovatie meestal voordeliger dan twee keer beginnen.

---

**H2: Badkamerontwerp en advies**

Hulp bij de keuzes vóór de werf begint.

**Wat u krijgt:** een indelingsvoorstel op schaal, advies over tegels, sanitair, verlichting en kleuren afgestemd op de ruimte en het lichtinval, en een materiaallijst die rechtstreeks in de offerte past. Zo weet u vooraf hoe de badkamer eruitziet en wat de keuzes kosten.

---

**H2: Toiletrenovatie**

Een apart toilet of gastentoilet renoveren we los of samen met de badkamer. Details, aanpak en prijsbepalende punten op de pagina [Toilet renoveren in Antwerpen](/toilet-renovatie-antwerpen/).

---

**H2: Wat de prijs bepaalt**

Voor elke renovatie spelen dezelfde factoren mee:

- oppervlakte en hoeveelheid muur- en vloertegels;
- of leidingwerk, elektriciteit en chape vernieuwd worden;
- het verplaatsen van toilet, douche of afvoer;
- de materiaalkeuze — tegels en sanitair in basis- of hoogsegment;
- extra's zoals vloerverwarming, nis, maatwerk meubel of een gebiliste inloopdouche;
- de bereikbaarheid van de woning (verdieping, lift, parkeren in de stad).

Een exacte prijs kan pas na een plaatsbezoek. Daarna krijgt u een gedetailleerde offerte waarin deze posten apart benoemd staan.

---

**H2: Offerte aanvragen**

Vertel ons kort wat u van plan bent, dan plannen we een gratis plaatsbezoek in.

[Knop: **Plaatsbezoek aanvragen** → /contact/] · Of bel [+32 491 98 02 72](tel:+32491980272)

#### E. Conversion optimisation
- **Primary CTA:** "Plaatsbezoek aanvragen" (after each service section + closing)
- **Secondary CTA:** phone link; internal link to P6
- **Trust elements:** the "wat we eerst controleren" honesty ("we'll tell you if a partial job is a false economy"); named work sequence; transparent price-driver list
- **Objection handling:** "do I need a full renovation?" (deelrenovatie section), "why can't you just give a price?" (Wat de prijs bepaalt)
- **Contact opportunities:** one CTA per section anchor

#### F. Internal linking
- **Out:** → `/toilet-renovatie-antwerpen/` ("Toilet renoveren in Antwerpen"), → `/faq/` ("prijsbepalende factoren", "hoe lang duurt het"), → `/contact/` (CTAs)
- **In:** from P1 "Onze diensten in het kort", from P6 ("bekijk alle diensten"), from P4 (answers linking to the relevant service section anchor), nav + footer
- **Anchor text:** vary — "onze diensten", "wat een complete renovatie omvat", "deelrenovatie", not repeated exact-match

#### G. Structured data
- `WebPage` + `BreadcrumbList` (Home › Diensten)
- One `Service` node per offer (`serviceType` "Badkamerrenovatie" / "Badkamer deelrenovatie" / "Badkamerontwerp", `provider` → `…/#organization`, `areaServed` "Antwerpen")
- `inLanguage` `nl-BE`; fix `ImageObject` caption "badkamer renovatie nijmegen" → "badkamerrenovatie in Antwerpen"
- No `Offer`/price in schema (no fixed prices)

---

### PAGE P3 — Over ons (`/over-ons/`)

#### A. Page strategy
- **URL:** `/over-ons/`
- **Page type:** trust / about
- **Primary search intent:** commercial investigation & trust — "who are these people?"
- **Target audience:** a visitor who has read the offer and now wants to know who will be in their home and who they're contracting with
- **Primary topic:** who runs and does the work, and how they work
- **Primary keyword:** over Badkamer Renovatie Antwerpen (brand); secondary: badkamerrenovatie Antwerpen ervaring / wie voert de werken uit
- **Conversion goal:** move a warm visitor to P5
- **UVP:** a bathroom renovation run by a finishing contractor (Avant Garde Afbouw) whose core trades *are* tiling, screed and underfloor heating — the parts of a bathroom that fail when done badly
- **Differentiation:** honest about what the company is and is not; real people and qualifications instead of a counter animation

#### B. Recommended structure
1. `<h1>` **Over Badkamer Renovatie Antwerpen**
2. `<h2>` Wie wij zijn — operator (Avant Garde Afbouw), what we focus on, since when in Antwerp
3. `<h2>` Waarom een afbouwbedrijf uw badkamer doet — tegelwerk/chape/vloerverwarming as core trades
4. `<h2>` Ons team — named people / roles / qualifications `[FACT REQUIRED]`
5. `<h2>` Hoe wij werken — one contact point, fixed crew, written planning, clean site
6. `<h2>` Waarborg en verzekering — `[FACT REQUIRED]`
7. `<h2>` Kennismaken — CTA → P5

#### C. SEO elements
- **SEO title:** `Over ons | Badkamer Renovatie Antwerpen` (39)
- **Meta description:** `Badkamer Renovatie Antwerpen is onderdeel van afbouwbedrijf Avant Garde Afbouw. Lees wie de werken uitvoert, hoe we werken en welke waarborg u krijgt.` (150)
- **H1:** Over Badkamer Renovatie Antwerpen
- **Canonical:** `https://badkamerrenovatie.montegava.com/over-ons/`
- **OG title/description:** as above

#### D. Full original content (Dutch, ready to paste)

**H1: Over Badkamer Renovatie Antwerpen**

**H2: Wie wij zijn**

Badkamer Renovatie Antwerpen is onderdeel van **Avant Garde Afbouw**, een afbouwbedrijf gespecialiseerd in renovatiewerk voor particulieren en bedrijven. Onder deze naam voeren wij volledige en gedeeltelijke badkamer- en toiletrenovaties uit in Antwerpen en de omliggende districten. `[FACT REQUIRED FROM BUSINESS OWNER: sinds welk jaar voert u badkamerrenovaties uit in de regio Antwerpen? Vermeld een jaartal in plaats van "al jaren".]`

**H2: Waarom een afbouwbedrijf uw badkamer renoveert**

Een badkamer gaat het vaakst mis op de onzichtbare punten: een waterdichting die niet doorloopt, een chape zonder afschot, tegelwerk dat loskomt. Dat zijn net de kernstielen van een afbouwbedrijf. Tegelwerk, chapewerk en vloerverwarming behoren tot onze vaste activiteiten `[FACT REQUIRED FROM BUSINESS OWNER: bevestig deze lijst kernactiviteiten; de moederonderneming vermeldt stucwerk, schilderwerk, behangwerk, tegelwerk en vloerverwarming]`. Die ervaring passen we toe op de volledige badkamer.

**H2: Ons team**

`[FACT REQUIRED FROM BUSINESS OWNER: geef de namen en rollen van de vaste ploeg (bv. projectverantwoordelijke, tegelzetter, loodgieter), en eventuele kwalificaties/attesten (bv. getuigschrift tegelzetten, VCA, erkenning). Zonder deze gegevens blijft deze sectie leeg en wordt de kop verwijderd.]`

Wat wél vastligt: aan elk project is één vast aanspreekpunt gekoppeld, en dezelfde ploeg voert de opeenvolgende fasen uit — geen wisselende onderaannemers.

**H2: Hoe wij werken**

- **Eén aanspreekpunt** van het plaatsbezoek tot de oplevering.
- **Vaste ploeg** die uitbraak, techniek, tegelwerk en afwerking zelf uitvoert.
- **Planning vooraf** — u krijgt een dagenplanning vóór de start.
- **Nette werf** — afdekken, dagelijkse opkuis, en opkuis bij oplevering.
- **Duidelijke offerte** — posten apart benoemd, geen onverwachte meerwerken voor zaken die vooraf zichtbaar waren.

**H2: Waarborg en verzekering**

`[FACT REQUIRED FROM BUSINESS OWNER: welke waarborgtermijn geeft u schriftelijk op de uitgevoerde werken? Bent u verzekerd voor burgerlijke aansprakelijkheid uitbating en tienjarige aansprakelijkheid? Geef verzekeraar/polisnummer indien u dit wil tonen. Vermeld ook uw KBO- en btw-BE-nummer.]`

**H2: Kennismaken**

Wil u weten of we bij uw project passen? Vraag een gratis plaatsbezoek aan; dan bekijken we de badkamer en bespreken we de aanpak.

[Knop: **Plaatsbezoek aanvragen** → /contact/]

#### E. Conversion optimisation
- **Primary CTA:** "Plaatsbezoek aanvragen"
- **Trust elements:** operator named; the "why a finishing contractor" argument is concrete and checkable; process specifics; `[FACT REQUIRED]` slots for the strongest signals (team, qualifications, insurance, warranty, KBO)
- **Objection handling:** "who actually turns up" (Ons team / vaste ploeg), "are they legit / covered" (Waarborg en verzekering)
- **Do NOT include:** "0+ jaar ervaring" counter, "500+ renovaties", "5.0"

#### F. Internal linking
- **Out:** → `/diensten/` ("volledige en gedeeltelijke … renovaties"), → `/contact/` (CTA), → `/faq/` ("waarborg" → FAQ garantie answer)
- **In:** from P1 trust context ("wie voert de werken uit"), P5 ("meer over ons team"), nav + footer

#### G. Structured data
- `AboutPage` (or `WebPage`) + `BreadcrumbList` (Home › Over ons)
- `Organization` node consistent with other pages; add `parentOrganization` {"@type":"Organization","name":"Avant Garde Afbouw"}
- `inLanguage` `nl-BE`
- Add `employee`/`founder` to `Organization` **only** when real names are supplied

---

### PAGE P4 — Veelgestelde vragen (`/faq/`)

#### A. Page strategy
- **URL:** `/faq/`
- **Page type:** informational (pre-purchase Q&A)
- **Primary search intent:** informational — specific blockers before contacting a renovator
- **Target audience:** a homeowner far enough along to have concrete worries: price drivers, duration, permits, apartment rules, VAT, living through the works
- **Primary topic:** the practical and regulatory questions around renovating a bathroom in Antwerp
- **Primary keyword:** badkamerrenovatie Antwerpen — veelgestelde vragen
- **Secondary topics:** vergunning/melding badkamer Antwerpen · VME/syndicus · 6% vs 21% btw · asbestattest · duur · prijsdrijvers · bewoonbaarheid tijdens werken · waterdichtingsgarantie
- **Conversion goal:** clear the last objections, then → P5
- **UVP vs competitors:** most local pages answer only "wat kost het / hoe lang" in vague terms; this page is the only one covering permits, VME rules, VAT and asbestos honestly
- **Differentiation:** Antwerp/Flanders-specific regulatory answers; no wording overlap with the home mini-FAQ

#### B. Recommended structure
1. `<h1>` **Veelgestelde vragen over badkamerrenovatie in Antwerpen** (single H1)
2. Short intro line
3. Accordion, grouped:
   - **Prijs en duur:** prijsdrijvers · richtprijs · doorlooptijd · betaalschema
   - **Vergunningen en regels:** melding/omgevingsvergunning · appartement + VME/syndicus · asbestattest · 6% vs 21% btw
   - **Tijdens de werken:** badkamer/toilet bruikbaar · stof en toegang · parkeren werfzone
   - **Na de werken:** waarborg · onderhoud · wat bij een probleem
4. `<h2>` Nog een vraag? — CTA → P5

#### C. SEO elements
- **SEO title:** `Veelgestelde vragen over badkamerrenovatie in Antwerpen | Badkamer Renovatie Antwerpen` → final trim: `Veelgestelde vragen badkamerrenovatie Antwerpen | Badkamer Renovatie Antwerpen` (60)
- **Meta description:** `Prijs, duur, vergunningen, btw 6%, regels in een appartement en werken met een bewoonde woning: de praktische vragen over een badkamerrenovatie in Antwerpen, eerlijk beantwoord.` (176 → trim: `Prijs, duur, vergunningen, 6% btw en regels in een appartement: de praktische vragen over een badkamerrenovatie in Antwerpen, eerlijk beantwoord.` (144))
- **H1:** Veelgestelde vragen over badkamerrenovatie in Antwerpen
- **Canonical:** `https://badkamerrenovatie.montegava.com/faq/`
- **OG title/description:** as above

#### D. Full original content (Dutch, ready to paste)

**H1: Veelgestelde vragen over badkamerrenovatie in Antwerpen**

Hieronder de vragen die klanten in Antwerpen ons het vaakst stellen vóór ze beslissen. Staat uw vraag er niet bij, [neem gerust contact op](/contact/).

**H2: Prijs en duur**

**H3: Wat bepaalt de prijs van mijn badkamerrenovatie?**
De grootste posten zijn: de oppervlakte en de hoeveelheid tegelwerk, of het leidingwerk en de chape vernieuwd worden, het verplaatsen van toilet of afvoer, en uw keuze van tegels en sanitair (basis- of hoogsegment). Extra's zoals vloerverwarming, een nis of een maatwerk meubel tellen daar bovenop. Ook de bereikbaarheid speelt mee: een tweede verdieping zonder lift of parkeren in de binnenstad kost tijd.

**H3: Kunnen jullie een richtprijs geven?**
`[FACT REQUIRED FROM BUSINESS OWNER: wil u een richtprijs of prijsvork tonen (bv. "een volledige renovatie van een badkamer van 4–6 m² start doorgaans vanaf € X, exclusief sanitair en tegels")? Geef bedragen die u kunt onderbouwen. Zonder onderbouwde cijfers laten we hier enkel staan dat u na het plaatsbezoek een gedetailleerde offerte krijgt.]` Zonder onderbouwde bedragen: u krijgt na een gratis plaatsbezoek een gedetailleerde offerte waarin elke post apart benoemd staat.

**H3: Hoe lang duurt een volledige badkamerrenovatie?**
Voor een gemiddelde stadsbadkamer rekent u doorgaans op twee tot drie weken op de werf. De droogtijd van chape en waterdichting ligt grotendeels vast en kan niet worden versneld. Een deelrenovatie (bijvoorbeeld enkel de douche) duurt vaak enkele dagen. U krijgt de dagenplanning vóór de start.

**H3: Hoe verloopt de betaling?**
`[FACT REQUIRED FROM BUSINESS OWNER: geef uw betaalschema (bv. voorschot bij bestelling, tussentijdse schijf, saldo bij oplevering) en de betaaltermijn. Dit hoort ook in de algemene voorwaarden.]`

**H2: Vergunningen en regels**

**H3: Heb ik een vergunning nodig om mijn badkamer te renoveren?**
Voor een badkamerrenovatie binnen de bestaande ruimte — zelfde indeling, geen ingrepen aan de structuur of de gevel — is in Vlaanderen doorgaans **geen omgevingsvergunning en geen melding** nodig. Zodra u draagmuren wijzigt, de indeling van de woning aanpast, een raam of verluchting in de gevel maakt, of werken uitvoert aan een pand in een beschermd stadsgezicht, kan dat anders liggen. Twijfelt u, dan verwijzen we u naar de dienst Omgevingsvergunningen van de stad Antwerpen. Wij dienen zelf geen vergunningsaanvragen in.

**H3: Ik woon in een appartement. Waar moet ik op letten?**
De standleidingen voor water en afvoer zijn gemeenschappelijk en lopen door meerdere appartementen. Werken die daaraan raken, of aan de vloeropbouw boven een buur, vallen onder het reglement van de VME. Vraag vooraf **schriftelijke toestemming aan de syndicus**. Wij bezorgen u op verzoek een korte technische omschrijving van de geplande werken die u bij die aanvraag kunt voegen. Hou ook rekening met de uren waarop lawaaierige werken zijn toegelaten volgens het reglement.

**H3: Geldt het verlaagde btw-tarief van 6%?**
Voor renovatiewerken aan een woning die **ouder is dan tien jaar** en hoofdzakelijk als privéwoning wordt gebruikt, geldt onder de fiscale voorwaarden het verlaagde tarief van 6% btw op de werken (in plaats van 21%). De voorwaarden en de attestering verlopen volgens de FOD Financiën. `[FACT REQUIRED FROM BUSINESS OWNER: bevestig dat u met het 6%-tarief werkt en hoe u de klantverklaring/attest afhandelt op de factuur.]`

**H3: Heb ik een asbestattest nodig?**
Een asbestattest is in Vlaanderen verplicht bij de **verkoop** van een woning gebouwd vóór 2001, niet louter om te renoveren. Wél belangrijk: in woningen van vóór pakweg 2001 kan asbest zitten in oude vloerbekleding, lijmlagen of leidingisolatie. Komen we bij de uitbraak verdacht materiaal tegen, dan leggen we het werk stil en laten we het onderzoeken; verwijdering gebeurt door een gespecialiseerde firma. `[FACT REQUIRED FROM BUSINESS OWNER: werkt u hiervoor met een vaste asbestverwijderaar? Zo ja, welke rol neemt u op — coördinatie of enkel doorverwijzing?]`

**H2: Tijdens de werken**

**H3: Kan ik mijn badkamer of toilet gebruiken tijdens de renovatie?**
Bij een volledige renovatie is de badkamer een aantal dagen niet bruikbaar. Is er een tweede toilet in de woning, dan houden we dat zo lang mogelijk beschikbaar. Bij een aparte toiletrenovatie plannen we de dagen zonder toilet zo kort mogelijk en spreken we vooraf een oplossing af.

**H3: Hoeveel stof en overlast geeft dat?**
Uitbraak en het frezen van sleuven geven stof. We schermen de werfzone af met stofschotten, dekken looppaden af en kuisen dagelijks op. Volledig stofvrij bestaat niet bij uitbraakwerk, maar het blijft beperkt tot de werkzone.

**H3: Waar parkeren jullie voor materiaal en afvoer?**
Voor werven in de binnenstad of in smalle straten vragen we waar nodig een **parkeervergunning voor de werfzone** aan bij de stad, zodat er plaats is voor levering en containerafvoer. `[FACT REQUIRED FROM BUSINESS OWNER: rekent u de kost van de werfzonevergunning en de container door, of zit dat in de offerte?]`

**H2: Na de werken**

**H3: Welke waarborg krijg ik?**
`[FACT REQUIRED FROM BUSINESS OWNER: geef de schriftelijke waarborgtermijn op de uitgevoerde werken en wat eronder valt (bv. waterdichting, tegelwerk, sanitair). Vermeld of u onder de wettelijke tienjarige aansprakelijkheid voor structurele elementen valt.]` Wat vastligt: de waterdichting wordt volgens de regels van goed vakmanschap uitgevoerd en getest vóór het tegelwerk.

**H3: Wat bij een probleem na de oplevering?**
Meld het via het contactformulier of telefonisch. We komen kijken en herstellen wat onder de waarborg valt. `[FACT REQUIRED FROM BUSINESS OWNER: binnen welke termijn reageert u op een waarborgmelding?]`

**H2: Nog een vraag?**

[Knop: **Stel uw vraag / vraag een plaatsbezoek** → /contact/] · Of bel [+32 491 98 02 72](tel:+32491980272)

#### E. Conversion optimisation
- **Primary CTA:** contact/plaatsbezoek at the end + a lighter inline "[neem gerust contact op]" in the intro
- **Trust elements:** the regulatory answers signal genuine local expertise; admitting "wij dienen zelf geen vergunningsaanvragen in" and "volledig stofvrij bestaat niet" builds credibility
- **Objection handling:** this whole page is objection handling — price uncertainty, permits, apartment restrictions, VAT cost, disruption, after-care
- **Placement of social proof:** none here (keep it purely informational); link to P3 for trust

#### F. Internal linking
- **Out:** → `/contact/` (CTAs), → `/diensten/#complete` and `/diensten/#deelrenovatie` (from price/duration answers: "meer over wat een volledige renovatie omvat"), → `/toilet-renovatie-antwerpen/` (from the "badkamer of toilet gebruiken" answer), → `/over-ons/` (from "welke waarborg" → "meer over onze werkwijze en verzekering")
- **In:** from P1 mini-FAQ ("Alle veelgestelde vragen"), P2 ("hoe lang duurt het", "wat de prijs bepaalt"), P6 ("veelgestelde vragen"), nav + footer
- **Anchor text:** question-shaped where natural ("heb ik een vergunning nodig?"), not exact-match keyword strings

#### G. Structured data
- `FAQPage` with **every** visible Q&A, `text` matching the rendered answer verbatim (including the "zonder onderbouwde bedragen…" fallback wording that remains after a marker is deleted)
- `BreadcrumbList` (Home › Veelgestelde vragen)
- `inLanguage` `nl-BE`
- Remove the current Nijmegen-town answer entirely from both the page and the schema
- If a `[FACT REQUIRED]` marker is left unfilled, its answer must still be a complete, truthful sentence in both the page and the schema (no bracketed text in `FAQPage.text`)

---

### PAGE P6 — Toilet renoveren in Antwerpen (`/toilet-renovatie-antwerpen/`) — NEW

Replaces `/toilet-renovatie-nijmegen/` (lorem-ipsum 404). All footer/menu links
repointed; old directory removed; 301 documented in §11.

#### A. Page strategy
- **URL:** `/toilet-renovatie-antwerpen/`
- **Page type:** service detail (commercial-local)
- **Primary search intent:** commercial + local — "toilet renoveren Antwerpen"
- **Target audience:** homeowner who wants the separate toilet / gastentoilet done, sometimes as a smaller standalone job, sometimes alongside the bathroom
- **Primary topic:** renovating a separate toilet room in an Antwerp home
- **Primary keyword:** toilet renoveren Antwerpen
- **Secondary topics:** inbouwreservoir / hangtoilet · tegelwerk klein oppervlak · fonteintje · ventilatie zonder raam · combineren met de badkamer · prijsdrijvers · duur
- **Conversion goal:** request an offerte / plaatsbezoek
- **UVP:** a small room done properly — right reservoir, proper waste connection, tiling that suits a 1–2 m² space, and ventilation for a toilet without a window
- **Differentiation:** genuinely about the *separate toilet*, not a shrunk copy of the bathroom page

#### B. Recommended structure
1. `<h1>` **Toilet renoveren in Antwerpen**
2. Intro (2 sentences)
3. `<h2>` Wat een toiletrenovatie omvat
4. `<h2>` Los renoveren of samen met de badkamer
5. `<h2>` Oplossingen voor een kleine ruimte
6. `<h2>` Wat de prijs en de duur bepalen
7. `<h2>` Veelgestelde vragen (2–3, distinct from P4)
8. `<h2>` Offerte aanvragen — CTA → P5

#### C. SEO elements
- **SEO title:** `Toilet renoveren in Antwerpen | Badkamer Renovatie Antwerpen` (57)
- **Meta description:** `Uw apart toilet of gastentoilet renoveren in Antwerpen: inbouwreservoir, tegelwerk, fonteintje en ventilatie. Los of samen met de badkamer. Vraag een offerte aan.` (159 → trim: `Uw apart toilet of gastentoilet laten renoveren in Antwerpen: inbouwreservoir, tegelwerk en ventilatie, los of samen met de badkamer. Vraag een offerte aan.` (154))
- **H1:** Toilet renoveren in Antwerpen
- **URL slug:** `/toilet-renovatie-antwerpen/`
- **Canonical:** `https://badkamerrenovatie.montegava.com/toilet-renovatie-antwerpen/`
- **Robots:** `index, follow`
- **OG title/description:** as above

#### D. Full original content (Dutch, ready to paste)

**H1: Toilet renoveren in Antwerpen**

Een apart toilet is klein, maar de renovatie ervan vraagt dezelfde zorg als een badkamer: de juiste afvoeraansluiting, een reservoir dat past, tegelwerk op maat van een krappe ruimte en werkende ventilatie. Wij renoveren uw toilet of gastentoilet in Antwerpen, los of samen met de badkamer.

[Knop: **Offerte aanvragen** → /contact/]

**H2: Wat een toiletrenovatie omvat**

- **Uitbraak** van het bestaande toilet, de tegels en waar nodig de vloeropbouw.
- **Aanpassing van aan- en afvoer**: correcte diameter en afschot van de afvoer, aansluiting op de standleiding.
- **Inbouwreservoir en hangtoilet** in een voorzetwand, of een klassiek staand toilet als de ruimte of de leidingaanleg dat vraagt.
- **Tegelwerk of alternatieve wandafwerking**, afgestemd op het kleine oppervlak.
- **Fonteintje** met koudwateraansluiting.
- **Verlichting en een stopcontact** waar gewenst.
- **Ventilatie**: een mechanische afzuiging voor een toilet zonder raam, met doorvoer naar buiten of naar het bestaande systeem.
- **Afwerking**: plafond, schilderwerk, deur, en opkuis bij oplevering.

**H2: Los renoveren of samen met de badkamer**

Ligt het toilet naast of in de buurt van de badkamer, dan is samen renoveren meestal voordeliger: één keer uitbraak, gedeeld leidingwerk, dezelfde tegels en één werfopstelling. Een apart gastentoilet op het gelijkvloers renoveren we doorgaans als losse opdracht van enkele dagen. Wat in uw geval het meest zinvol is, zeggen we na het plaatsbezoek.

**H2: Oplossingen voor een kleine ruimte**

- Een **hangtoilet** maakt de vloer vrij en oogt ruimer; de voorzetwand kost enkele centimeters diepte maar levert een nis of een smalle plank op.
- **Grotere tegels** met dunne voegen maken een smal toilet visueel rustiger.
- Een **hoekfonteintje** of een smal model houdt de doorgang vrij.
- Een **schuifdeur** of een naar buiten draaiende deur wint bruikbare ruimte.

**H2: Wat de prijs en de duur bepalen**

De prijs hangt af van: of de afvoer verplaatst of aangepast wordt, de keuze tussen inbouw- en staand toilet, de hoeveelheid en het type tegelwerk, het bijplaatsen van ventilatie, en de bereikbaarheid van de woning. Een losse toiletrenovatie duurt doorgaans **twee tot vier werkdagen**, plus droogtijd wanneer er een nieuwe chape of waterdichting nodig is. Een exacte prijs volgt na een plaatsbezoek, in een gedetailleerde offerte.

**H2: Veelgestelde vragen**

**H3: Kan het toilet blijven werken tijdens de renovatie?**
Tijdens de werken is het toilet enkele dagen buiten gebruik. Is er een tweede toilet of een badkamer met toilet in de woning, dan plannen we daarrond. Anders spreken we vooraf een tijdelijke oplossing af.

**H3: Kan een hangtoilet in elke woning?**
Meestal wel. Er moet plaats zijn voor een voorzetwand (ongeveer 15–20 cm diepte) en het inbouwframe moet stevig kunnen worden bevestigd. In oudere woningen met een lichte scheidingswand voorzien we een verstevigd frame tot op de vloer.

**H3: Renoveren jullie ook enkel het toilet in een appartement?**
Ja. Hou er rekening mee dat werken aan de gemeenschappelijke standleiding onder het VME-reglement vallen; vraag vooraf toestemming aan de syndicus. Zie ook onze [veelgestelde vragen](/faq/).

**H2: Offerte aanvragen**

Vertel ons kort wat u wil, dan plannen we een gratis plaatsbezoek.

[Knop: **Plaatsbezoek aanvragen** → /contact/] · Of bel [+32 491 98 02 72](tel:+32491980272)

#### E. Conversion optimisation
- **Primary CTA:** "Offerte aanvragen" / "Plaatsbezoek aanvragen" (hero + close)
- **Secondary CTA:** phone link; link to `/diensten/` and `/faq/`
- **Trust elements:** specific small-space know-how; the "samen is voordeliger" honesty; VME note shows local awareness
- **Objection handling:** disruption (toilet out of use), feasibility (hangtoilet in an old wall), apartment rules
- **Social proof:** a real before/after of a small Antwerp toilet, once available

#### F. Internal linking
- **Out:** → `/contact/` (CTAs), → `/diensten/` ("los of samen met de badkamer" → complete renovation), → `/faq/` ("veelgestelde vragen", VME note)
- **In:** P1 ("Toilet renoveren in Antwerpen"), P2 (toilet section), P4 (disruption answer), **every footer** (replace "Toilet renovatie" → "Toilet renovatie Antwerpen" pointing here), nav
- **Anchor text:** "toilet renoveren in Antwerpen", "toiletrenovatie", "een apart toilet renoveren"

#### G. Structured data
- `WebPage` + `BreadcrumbList` (Home › Toilet renoveren in Antwerpen)
- `Service` (`serviceType` "Toiletrenovatie", `provider` → `…/#organization`, `areaServed` "Antwerpen")
- `FAQPage` for the 3 on-page Q&A (text matches verbatim)
- `inLanguage` `nl-BE`
- Reuse the shared `Organization` node

---

### PAGES P7 / P8 — Legal (`/privacy-policy/`, `/algemene-voorwaarden/`)

**Treatment: light pass now, legal review required before relying on them.**

Do now (no legal judgement needed):
- `<html lang="nl-BE">`, `og:locale` `nl_BE`, absolute canonical, keep `noindex, follow`.
- Fix the `<title>` casing: "privacy policy" → "Privacybeleid".
- Replace the stray entity names ("Badkamer Renovatie Centrum", any "Amsterdam") with "Badkamer Renovatie Antwerpen (onderdeel van Avant Garde Afbouw)".
- Fix `Antwerpen<woord>` concatenations and mojibake.
- Replace `[01-01-2024]` placeholder with a real "laatst bijgewerkt" date on publication.
- Insert the correct identity/contact block (NAP + `[FACT REQUIRED: KBO- en btw-BE-nummer]`, verwerkingsverantwoordelijke, contact-e-mail voor privacyverzoeken).
- Add a visible banner at the top of both pages:
  `[FACT REQUIRED FROM BUSINESS OWNER: deze tekst is een sjabloon. Laat privacybeleid en algemene voorwaarden nakijken door een jurist tegen de GDPR en tegen het Wetboek van economisch recht (Boek VI – marktpraktijken en consumentenbescherming), inclusief wettelijke garantie van 2 jaar, informatieplichten en de regeling rond het herroepingsrecht bij werken in een woning.]`

Do NOT (needs a lawyer): rewrite the substantive clauses, assert specific
retention periods, warranty scope, payment/withdrawal terms, or dispute
resolution. `AboutPage`/`WebPage` schema: fix `name` + `inLanguage` only.
