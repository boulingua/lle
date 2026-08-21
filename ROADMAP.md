# LLE — Latin course roadmap

> boulingua Latin course · repo code `lle` · signature accent `#C72334` (light) / `#E77E89` (dark) · pentagon mark.
> Status today: empty scaffold (LICENSE, README, brand icons), flagged **coming soon** on the world map. This document is the plan to build the whole thing — content and website — on the pagegen standard and the boulingua curriculum framework.

---

## 1. Overview

**What it is.** A free, openly-licensed course that teaches learners to **read classical Latin** — its morphology, syntax and canonical texts — for the German *Gesamtschule* system and for independent learners. Latin here is a **foreign/heritage language read for its texts and its role at the root of Europe's languages**, not a spoken one. The course follows the boulingua five-step unit model (Activate → Input → Practise → Apply → Reflect), ships committed slide decks / worksheets, and is CEFR-aligned **where the framework legitimately applies**.

**Target learners.** Secondary pupils working toward the *Latinum* / school Latin qualifications; adult self-learners and readers coming to Latin for history, law, medicine, theology or philology.

**Realistic CEFR scope.** Expressed as **reading stages** mapped to CEFR **reception** (and the linguistic + mediation domains), not the full A1–C2 communicative ladder. Target ceiling: **B2 reading** of unadapted classical prose and verse, with a C1-reading appreciation track declared aspirational.

**The 3–5 defining challenges (the language-specific reframe):**

1. **No native speakers, no living community.** The modern communicative A1–C2 apparatus (interaction, oral production, sociolinguistic appropriateness of a speech community, online transactions) has **no target** in a classical language. These domains are declared **out-of-scope-for-classical**, honestly and explicitly, not silently skipped.
2. **Reception-first by nature.** The course is overwhelmingly **reading, grammar, morphology and mediation (translation into a modern language)**. Conformance is reframed around the framework's **REC / LING / MED** scales.
3. **Copyright is an advantage, not a constraint.** Every primary text (Caesar, Cicero, Vergil, Ovid, the Vulgate, Catullus…) is **public domain**. Sister sites fight for openly-licensed input; Latin has an unlimited, citable corpus.
4. **Pronunciation is reconstructed, not attested.** Audio must choose between **restored classical** and **ecclesiastical** pronunciation, and there is **no Latin Piper voice at all** — verified, not assumed: the upstream `rhasspy/piper-voices` catalogue snapshot of 2026-08-21 holds 174 voices and **zero `la` records**. Synthetic audio is therefore closed, permanently. What stays open is whether to curate human recordings, and in which pronunciation (§2, §6, §9).
5. **"Level" is a reading stage, not a can-do age band.** Progression is grammatical and lexical (declensions → tenses → subjunctive → indirect statement → scansion), crosswalked to CEFR reception rather than driven by it.

---

## 2. Language & localisation decisions

Concrete, opinionated calls — each to be confirmed on first release.

- **Writing system.** Latin script — the learner's own alphabet. **No script-literacy barrier**, unlike Arabic/Japanese/Russian sister languages. **Decision: no separate alphabet-learning burden**, but keep a short **Level 0 onboarding** (below) for sound and orthography.
- **Orthography — macrons.** Vowel length is phonemic and pedagogically essential (`liber` book vs `līber` free; case endings). **Decision: macrons ON throughout teaching text and vocabulary; OFF in authentic quoted inscriptions/manuscripts where fidelity matters.** Use `ā ē ī ō ū ȳ` (precomposed Unicode); ligature *æ/œ* rendered as `ae/oe`. Interlinear/consonantal *u/v* and *i/j*: **decision: normalise to `u/v` distinction, `i` for consonantal i** (mainstream school convention), documented in the style note.
- **Variant / register.** **Classical (Golden/Silver Age) Latin as the spine.** Ecclesiastical/Medieval Latin offered as a **supplementary reading track** in later stages, not the default. No dialect fork.
- **RTL / bidi.** Not applicable.
- **Web fonts.** hugo-coder's default stack already covers Latin-with-macrons in modern system fonts. **Decision: keep the theme fonts; add a self-hosted, openly-licensed serif with full combining-macron + precomposed coverage** (e.g. an SIL/OFL face) for body text and worksheets, so macrons never fall back to tofu. Verify glyph coverage for `ā ē ī ō ū ȳ Ā Ē Ī Ō Ū` and `æ œ` in the QA gate.
- **Native voice / Piper TTS — settled: none, and not to be re-litigated.** `lle` carries `status: none` in **`audiogen/voices.yml`** (relocating to `kit/audio/voices.yml` at F1), the registry every course reads its voice ID from; voice IDs are never hand-typed anywhere, because a transliterated ID is how a 404 gets written into a download script. That row records the measurement behind the decision: the upstream `rhasspy/piper-voices` catalogue snapshot of 2026-08-21 contains 174 voices and **zero `la` records**. There is no Latin voice to audition, no second-choice Latin voice beneath it, and no licence question to resolve. Of the three options once listed: (a) **ship no synthetic audio** — this is the decision; (b) *approximate with an Italian or Spanish Piper voice tuned to ecclesiastical values* — **rejected and closed**, because a voice is never substituted from a neighbouring language, however close the phonology looks; (c) **curate openly-licensed human readings** (many restored-classical readings are CC-licensed) — the only route to Latin audio there is, and a post-MVP, opt-in enhancement for a small set of showcase texts. What remains open in §9 is the *pronunciation* choice and whether the curation is worth the effort — not the availability of a voice. The README's "native-voice audio" promise is reworded accordingly to "reconstructed-pronunciation audio, where available."
- **Level 0 — "Ianua" (script & sound onboarding).** A short pre-stage: alphabet review, **vowel length & macrons**, syllabification, **stress rules**, and a side-by-side of **restored-classical vs ecclesiastical** pronunciation so learners choose knowingly. 3–4 units. This is the Latin analogue of the script-onboarding stage other languages need for their writing systems.

---

## 3. Instantiation from pagegen

Stand up the buildable site first; author content into it second.

1. **Copy the template.** Instantiate `pagegen` into this repo's working tree (content model, layouts, scripts, `.github/workflows/build-deploy.yml`, legal scaffold, VG Wort resolver). Keep the existing `lle` `LICENSE`, `README.md` and `brand/` icons.
2. **Edit only the marked `hugo.toml` values:**
   - `baseURL = "https://boulingua.github.io/lle/"`
   - `title = "Latin — S. Le Boulanger"`
   - `languageCode = "la"` · `defaultContentLanguage = "en"` (UI/metalanguage is English/German; Latin is the object language)
   - `[params].navTitle = "Latin"` · `description` = a Latin-reading course line · `keywords = "Latin,Latinum,CEFR reception,reading,classical,grammar,OER"`
   - `[[params.social]].url = "https://github.com/boulingua/lle"`
   - `[params.plausible].domain = "boulingua.github.io/lle"`
   - `params.code = "lle"` ← selects the accent from `data/accents.yaml`
   - Replace the `[[menu.main]]` sections with the Latin section landings (Ianua, Stage I–IV, Materials, Appendices, About, Legal).
3. **Regenerate the pentagon.** `python brand/make_icon.py lle` → writes `brand/icon.svg/png`, `static/favicon-*.png`, `apple-touch-icon.png` in `#C72334`. Confirm the committed `lle/brand/icon.*` match (regenerate and overwrite from the canonical script rather than keeping hand-made copies).
4. **Confirm accent data.** `data/accents.yaml` already carries `lle` (`accent #C72334`, `hover #A01C2A`, `dark #E77E89`, `dark_hover #EFA9B0`) — verify, do not edit CSS.
5. **Fill legal placeholders.** Complete the ⟨…⟩ in `impressum` / `datenschutz` / `haftungsausschluss`; the Datenschutz page must carry the VG Wort METIS disclosure clause verbatim from the standard.
6. **First green build + Pages.** `hugo --minify --gc` clean; run the gate battery locally (`scripts/verify_*`); enable GitHub Pages via the workflow. **Definition of a passing scaffold:** builds with zero errors, one A1-stub unit + its exam render, VG Wort render/manifest gates pass on the stub, legal pages have no ⟨…⟩ left.

---

## 4. Curriculum conformance target

**Framework:** `boulingua-curriculum` (pin the version in the manifest). Latin is the **odd one out** — the framework's own *"Honest note on instantiation"* explicitly authorises declaring gaps, and that is exactly what a classical language does.

**Declared conformance level.** Target **`core`-depth coverage (A1–B1)** for the applicable domains, extending toward **B2 reception**, declared in the manifest as **`core-restricted`** with **`profile: classical-reception`** — the legal value for a conformance that is honest about whole domains having no classical target. We **cannot** claim `full`/`complete` — those require every in-scope scale including interaction and oral production, which have no classical target. The manifest declares this honestly.

**Scales implemented (mapped to descriptor IDs `{LEVEL}.{DOMAIN}.{SCALE}.{SEQ}`):**

- **REC (Reception) — primary.** `overall-reading-comprehension`, `reading-for-information-and-argument`, `reading-for-orientation`, `reading-instructions`, `reading-correspondence`, `reading-as-a-leisure-activity`, plus `identifying-cues-and-inferring` (the reception strategy — decisive for parsing inflected word order). Levels A1r–B2r.
- **LING (Linguistic competence) — primary.** `grammatical-accuracy`, `general-linguistic-range`, `vocabulary-range`, `vocabulary-control`, `orthographic-control`. `phonological-control` implemented **partially / reconstructed** (macrons, stress) and annotated as such.
- **MED (Mediation) — primary, the Latin sweet spot.** `translating-a-written-text` (the core Latin skill), `processing-text`, `relaying-specific-information`, `note-taking`, `analysis-and-criticism-of-creative-texts`, `expressing-a-personal-response-to-creative-texts`.
- **PROD (written, partial).** `reports-and-essays` / `overall-written-production` in the **modern metalanguage about Latin texts**, plus optional **prose composition** (Latin *written* production) at Stage III+.
- **PRAG (partial, receptive framing).** `coherence-and-cohesion`, `propositional-precision` as analytic reading competences.

**Scales declared out-of-scope-for-classical (documented, not silent):** all **oral REC** (understanding a live audience / audio media / conversation between speakers), **all INT** (conversation, discussion, transactions, online, correspondence-as-exchange), **oral PROD** (monologue, addressing audiences, announcements), **SOC** (sociolinguistic appropriateness of a speech community), **PLUR** interaction scales. Each gets a per-scale `out_of_scope_classical` entry with a one-line rationale ("no living speech community; classical language read, not spoken/negotiated").

**Machine-readable scope/coverage manifest.** Publish `conformance.yml` at the repo root (modelled on `curriculum/examples/de-a1/conformance.yml`): `framework`, `framework_version`, `language: la`, **`declared_conformance: core-restricted`** plus **`profile: classical-reception`** — `core (reception)` is not a legal value and must not be written — and a `scales:` table of `{scale, levels_covered, no-official-descriptor cells, out_of_scope_classical}`. Every unit's front-matter `curriculum.cefr_can_do` lists the descriptor IDs it realises.

**Gate.** The reusable workflow `boulingua/.github/.github/workflows/course-build.yml@v1` runs `python .curriculum/scripts/conformance_audit.py resolve --manifest conformance.yml --content content`, which is what confirms each ID is well-formed, unique, and resolves to a real (scale, level) in `scale-registry.yml`. `id-audit.sh` audits the framework's *own* level files and **cannot** validate this repo. Do not wire it here. **A silently missing in-scope scale is a failure; a declared out-of-scope one is honest — declare, don't hide.**

---

## 5. Content creation plan

Recurring cast & theme (Cambridge/Oxford-style): follow a **fictional Roman *familia*** — a household (paterfamilias, matrona, *liberi*, a *servus/paedagogus* narrator) — across the late Republic and early Empire, so vocabulary, culture and grammar recur in a continuous storyworld. Each stage carries a **civilisation thread** (daily life → politics → literature).

Reading stages, unit counts, effort tags (S ≤ ½ day, M ~1–2 days, L ~3–5 days per unit):

| Stage | CEFR reception | Grammar spine | Units | Effort |
|---|---|---|---|---|
| **L0 — Ianua** (onboarding) | pre-A1r | alphabet, macrons, syllable/stress, pronunciation variants | 3–4 | S–M |
| **Stage I — Tirones** | A1r | 1st/2nd decl. nouns, 1st/2nd conj. present, `esse`, simple syntax; adapted Latin | 10 | M |
| **Stage II — Discipuli** | A2r | remaining declensions, adjectives, pronouns, imperfect/future/perfect system | 10 | M |
| **Stage III — Lectores** | B1r | subjunctive intro, participles, ablative absolute, indirect statement; lightly-adapted authors | 12 | M–L |
| **Stage IV — Auctores** | B2r | full syntax, gerund/gerundive, conditionals, scansion; **unadapted** Caesar / Cicero / Ovid / Vergil | 10–12 | L |
| **(Stretch) Stage V — Periti** | C1r (aspirational) | literary/stylistic analysis, wider canon | declared, later | L |

**Per unit:** the five-step model, differentiated exercises with **answer keys** and **teacher notes**, a graded reading passage (adapted early, authentic later), a **vocabulary set** (drawn from a published high-frequency core, e.g. DCC/Diederich lists), morphology drill, and a **translation-into-modern** task (the MED core).

**Exams as first-class sibling bundles.** One **Probatio** per stage (`…-exam/` bundle, `page_type: exam`, shared `unit_nr` with a capstone unit), plus a mid-stage check from Stage II on. Each carries `duration_min`, `total_points`, `notenschluessel`, and a committed PDF under `static/downloads/<stage>/`.

**Appendices (first-class `page_type: appendix`):** full **morphology reference** (all declensions/conjugations, principal parts), **core vocabulary list**, **glossary**, **syntax/constructions reference**, **scansion guide** (Stage IV+), **civilisation/culture notes**, **translation rubric**, **teaching workflow**. Effort M each, built incrementally alongside the stages that need them.

**Acceptance criteria per phase:** every unit renders; all descriptor IDs in front-matter resolve (the §4 gate green); every unit + exam + appendix ≥1800 chars has a registered VG Wort mark; materials (deck + worksheet) committed with thumbnails; answer keys present; no ⟨…⟩ placeholders; clean `hugo --gc`.

---

## 6. Website & materials

- **Section landings** (`_index.md`, `page_type: section`) rendered **via shortcodes only — never raw HTML** — for L0/Ianua, each Stage, Materials, Appendices, About.
- **Materials pipeline.** Generate decks and worksheets **locally** from the branded **slidegen** (LaTeX Beamer) and **sheetgen** (LaTeX worksheet) templates, export **editable source + PDF**, and **commit** them under `static/materials/` and `static/downloads/`. CI **verifies presence + attribution only** (no TeX Live in the deploy path). Wire each into a unit's `presentation:`/`worksheet:` front-matter `{ file, thumbnail }`.
- **Thumbnails.** `render_thumbs.py` produces committed preview images for every deck/worksheet.
- **Downloads.** All PDFs + editable sources under `static/downloads/`; `verify_downloads.py` gate confirms every linked download exists and is attributed (CC BY-SA 4.0, source citation for any quoted public-domain text).
- **Audio (audiogen / Piper).** **No Latin Piper voice exists** — verified against the 174-voice upstream catalogue (zero `la` records) and recorded as `status: none` in `audiogen/voices.yml`, `kit/audio/voices.yml` from F1; see §2. **Plan:** the Piper pipeline is never run for `lle`. MVP ships **no audio at all**; a later opt-in phase adds **curated openly-licensed human recordings** (restored-classical) for showcase passages, delivered as OGG/Opus through the audiogen structure and attributed like any other openly-licensed source. Substituting an Italian or Spanish voice is **not** a fallback and is closed (§2). What §9 still decides is the pronunciation of the curated recordings, not whether to synthesise.
- **Public-domain corpus.** Every primary text is quoted from a **cited public-domain edition** (Perseus/PHI/The Latin Library provenance recorded); the copyright advantage means authentic texts appear from Stage III with no licensing friction.

---

## 7. VG Wort — pixel assignment for ALL content pages (required, non-skippable)

**Binding standard** (`pagegen/docs/vgwort-standard.md`). **Every** original creative page ≥ **1800 characters** of rendered prose gets **exactly one** VG Wort Zählmarke, on exactly one URL:

- **Which pages:** every **unit**, every **exam**, every **appendix**, and every long-form **editorial** page (about, get-started, civilisation essays, acknowledgements, references intro) that reaches the *Mindestumfang*.
- **Which pages never get one:** the home page, the Materials hub and other navigation/index/tag pages, paginated continuations, and the **templated legal pages** (Impressum / Datenschutz / Haftungsausschluss).
- **Process per work:** draw a **fresh public code** (32-hex `Öffentlicher Identifikationscode`) from the author's **T.O.M.** account → register it in `data/vgwort.yaml` keyed by the page `url:`/`path:` (`public_id`, `pixel_url: https://vg09.met.vgwort.de/na/<code>`, `min_chars: 1800`, `author`, `registered_at`) → it renders through the **shared resolver** (`layouts/_partials/vgwort/url.html`) as a `<head>` preload + eager `<body>` `<img>` (JS-free, no consent gate, `loading="eager"`, off-screen not `display:none`) → **record it in the private usage registry** (kept outside the repo). **Never invent codes; never expose the private code; never reuse a code across pages.**
- **Gates:** coverage audit (warning — flags any ≥1800-char editorial page without a mark), rendered-pixel verify (blocking — each registered pixel appears on exactly one URL), hub guard (blocking — `met.vgwort.de` absent from the Materials hub). Exclude `vgwort.de` from the link-checker.
- **Estimated total marks needed:** L0 (≈3) + Stage I–IV units (≈42) + Stage V stretch (≈8) + exams (≈6) + appendices (≈8) + long-form editorial (≈8) ≈ **70–80 Zählmarken** over the full course lifetime; **~15–18 needed for the MVP** (L0 + Stage I + its exam + first appendices + about). Draw codes in batches per phase.

---

## 8. Milestones & sequencing

- **M0 — Scaffold green (§3).** Template instantiated, `hugo.toml` set, pentagon regenerated, legal filled, one stub unit + exam, all VG Wort/legal/download gates pass. *Dependency: none.*
- **M1 — L0 Ianua live.** 3–4 onboarding units, pronunciation reference appendix, first decks/worksheets, marks registered. *Dep: M0.*
- **M2 — MVP: Stage I complete + Probatio I.** 10 A1r units, exam bundle, core-vocabulary + morphology appendix seeds, materials committed, `conformance.yml` published at the repo root declaring `core-restricted` / `profile: classical-reception` scope, green under the §4 gate. **← This is the flip point.**
- **M3 — Stage II + exam.** A2r; extend morphology/glossary appendices.
- **M4 — Stage III + exam.** B1r; introduce authentic adapted texts, translation rubric, syntax reference.
- **M5 — Stage IV + exam.** B2r; unadapted classical authors, scansion guide; conformance extended to B2 reception.
- **M6 — Enhancements.** Curated audio (if pursued), Stage V/C1-reading stretch, ecclesiastical/medieval supplementary track, civilisation essays.

**Suggested cadence** (single author, LLM-assisted for non-authorial tasks only): M0–M1 in the first working block; then roughly one stage per sustained content push, appendices growing alongside.

**Definition of "done → flip from coming-soon to active on the world map":**
1. **M2 reached** — L0 + Stage I + Probatio I fully authored, with answer keys and teacher notes;
2. every content page has committed **materials** (deck + worksheet + thumbnails) and, where in scope, downloads;
3. **all in-scope descriptor IDs resolve** (the §4 gate green) and `conformance.yml` is published with the honest out-of-scope-for-classical declarations;
4. **every ≥1800-char page carries a registered VG Wort mark**; render/manifest/hub gates green; legal pages complete;
5. clean `hugo --minify --gc` build deployed to GitHub Pages;
6. README status line updated from "scaffold" to active, and the hub `website` world-map entry switched from *coming soon* to live.

---

## 9. Open decisions & risks (language-specific)

- **Audio pronunciation & source — narrowed, and half of it closed.** The synthetic branch is **shut**: no Latin voice exists upstream (174 voices, zero `la`), and a neighbouring language's voice is never substituted, so `lle` carries `status: none` in the voice registry and no future audition can reopen it. This is verified ground, not a pessimistic assumption, and it should stop being re-argued. What is still open: **restored-classical vs ecclesiastical** for curated human recordings, and whether that curation is worth the effort at all. **Leaning: no MVP audio; add curated openly-licensed restored-classical recordings later.** Affects the README "native-voice audio" promise, which must be reworded now.
- **Conformance framing acceptance.** The framework has no first-class "classical language" mode; we extend `no-official-descriptor` / `out-of-scope` with an `out_of_scope_classical` rationale. **Risk:** the resolve gate only checks *implemented* IDs — the *completeness* obligation sits on the conformance doc, so the manifest must be scrupulously explicit or the gaps read as omissions. `profile: classical-reception` names the shape; consider upstreaming it as a first-class `classical` profile to the curriculum repo.
- **Macron & orthography policy** (u/v, i/j, ae/oe, when to drop macrons for authentic text) must be fixed **before** authoring Stage I to avoid costly reflow; capture it in a style appendix.
- **Metalanguage.** Glosses/instructions in **English or German** (the *Gesamtschule* audience is German). **Leaning: German-first for school alignment, English parallel where effort allows.** `defaultContentLanguage` and menu strings depend on this.
- **Grammar sequence / textbook lineage.** Inductive reading-method (Cambridge/*Lingua Latina per se Illustrata*) vs grammar-translation. **Leaning: reading-method spine with explicit grammar reference appendices** — plays to the reception-first framing.
- **Web-font macron coverage.** Verify the chosen OFL serif renders all macron + `æ/œ` glyphs in body, decks and worksheets; add a QA check.
- **Scope creep into oral revival.** "Living Latin" / spoken-Latin communities exist; resist pulling INT/PROD-oral scales back in scope for MVP — keep them declared out-of-scope-for-classical unless a deliberate later track is decided.
