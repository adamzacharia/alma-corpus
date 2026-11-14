# ALMA Corpus

A structured, evidence-checked corpus of **5,173 refereed astronomy papers (2012–2026) that use data from ALMA**, the Atacama Large Millimeter/submillimeter Array. Each processed paper gets a **methods card**: a schema-validated record of what data the authors used, how they calibrated and imaged it, which analysis steps and software they ran, what they measured, and what they claimed. Every fact on a card is backed by a verbatim quote from the paper.

From those cards the corpus builds:

- a **tabular catalog** (Parquet) of papers, ALMA datasets, software, analysis steps, numeric results and claims;
- **46 technique skills**: how-to guides for ALMA analysis tasks (self-calibration, moment maps, Keplerian disk fits, lens modelling, …), each built from what tens to thousands of real papers actually did;
- corpus-wide **statistics** on software use, settings and how often papers leave details unstated.

The goal is to teach AI research agents how ALMA papers are actually done, to build answer keys for reproducing published analyses, and to identify which data, software and settings a reproduction needs.

> **What is not in this repository:** `raw/` (~50 GB of downloaded PDFs and LaTeX source archives) and `text/` (~9.8 GB of extracted full text and figures) are excluded by `.gitignore` because they exceed GitHub's size limits. Paths in the manifest and cards that point there will not resolve in a fresh clone.

---

## At a glance

| | |
|---|---|
| Papers in manifest | 5,173 (ADS snapshot 2026-10-27; 5,172 refereed) |
| Publication years | 2012 – 2026 |
| Papers with evidence-verified cards | 3,539 (`status = evidence_ok`) |
| Papers in the catalog | 3,500 (2,826 full-depth, 674 light-depth) |
| Card files | 3,674 `card.json` across 4,006 paper folders (some papers carded by several models) |
| Distinct ALMA project codes | 2,675 (7,387 paper–project links) |
| Software mentions | 14,443 |
| Analysis steps | 19,136 |
| Numeric results | 42,037 |
| Claim tuples | 11,105 |
| Technique skills | 46 |
| Held-out benchmark papers | 17 (marked `heldout = 1`, excluded from skills) |

**Top journals:** ApJ (1,797), A&A (1,355), MNRAS (826), ApJL (546), AJ (136), PASJ (98), ApJS (71), Nature Astronomy (68).

**Papers per year:** growing from 19 in 2012 to 579 in 2025 (402 so far in 2026).

**Data provenance mix:** PI data 3,516 · archival only 806 · archival + PI 786 · unknown 65.

**Most-used software** (non-held-out cards): CASA, Astropy, tclean, emcee, RADEX, GILDAS, SciPy, Matplotlib, MIRIAD, NumPy, APLpy, RADMC-3D, AIPS, CASSIS, astrodendro, GALFIT.

---

## Repository layout

```
alma-corpus/
├── manifest.sqlite        # Master state database: every paper, fetch, model call and status change
├── catalog/               # Flattened Parquet tables built from verified cards
├── cards/                 # One folder per paper, one subfolder per model that carded it
├── skills/                # 46 technique skills + per-skill source packs + corpus stats
├── skills_backup_before_3500_refresh/   # Earlier skill versions (38 skills) before the 3,500-paper rebuild
├── batches/               # Batch API request files (JSONL) for card, figure and repair runs
├── selections/            # Bibcode lists defining which papers went into each production run
├── pilot/                 # Model-comparison pilot (Haiku vs Sonnet vs Opus) and cost estimate
├── sources/               # Upstream metadata snapshots: ADS, arXiv API, ALMA ObsCore
├── logs/                  # Run logs for download, extraction, carding and skill builds
├── raw/                   # (not in git) PDFs + LaTeX source, sharded by hash prefix 00–ff
└── text/                  # (not in git) Extracted full text, page maps and figures per paper
```

Paper folders are named by **ADS bibcode**, URL-encoded (`&` → `%26`), e.g. `cards/2016MNRAS.457.4536W/` or `cards/2012A%26A...538A..44D/`.

---

## `manifest.sqlite`

The single source of truth for the pipeline. Open it read-only:

```python
import sqlite3
con = sqlite3.connect("file:manifest.sqlite?mode=ro", uri=True)
```

| Table | Rows | Contents |
|---|---|---|
| `papers` | 5,173 | One row per paper: ADS metadata (title, authors, abstract, journal, DOI, arXiv ID), ALMA project codes, archival class, licence, text source and quality, card model/schema, pipeline status |
| `events` | 37,416 | Every status transition per paper (`from_status` → `to_status`, timestamp, note) |
| `fetches` | 10,519 | Every download attempt: host, URL, HTTP status, outcome, bytes, duration |
| `batches` | 93 | Batch API jobs: model, schema version, request count, submit/collect times |
| `shred_requests` | 3,275 | Individual card requests: model, run, batch, status, estimated and actual cost |
| `spend` | 3,903 | Token usage per model call (input, output, cache read/write) |
| `kv` | 2 | Schema version and snapshot metadata (ADS snapshot ID, ObsCore TAP mirror and row count) |

**Paper status values** (`papers.status`):

| Status | Count | Meaning |
|---|---|---|
| `evidence_ok` | 3,539 | Card written and passed evidence verification |
| `extracted` | 1,433 | Full text extracted, not yet carded |
| `no_open_copy` | 85 | No open-access copy found |
| `resolved` | 82 | Metadata resolved, text not yet fetched |
| `shredded` | 31 | Card written, not yet verified |
| `retry_later` | 3 | Transient fetch failure |

**Text sources:** 4,562 from LaTeX source and 444 from PDF. Copies came from arXiv (4,939), Unpaywall (57) and publishers (10). Extraction quality: 3,918 good, 1,086 fair, 2 poor.

---

## `cards/` — methods cards

```
cards/<bibcode>/<model>/
├── card.json             # The structured card (schema 1.0)
├── card.md               # Human-readable rendering of the same card
├── evidence_check.json   # Quote and fact verification results
├── raw_response.json     # Raw model API response
├── prompt.md / reply.txt # Prompt and reply (for subagent-based runs)
├── usage_plan.json       # Token budget plan
└── repair_*              # Repair pass, if the first card failed validation
```

**Model subfolders:**

| Folder | Papers | Model |
|---|---|---|
| `sonnet` | 2,339 | Claude Sonnet 5.5 (Batch API) — main production run |
| `gemini4argon` | 922 | Gemini 4 Argon |
| `sonnetcc` | 566 | Claude Sonnet 5.5 via Claude Code subagents |
| `gpt61sol` | 189 | GPT-6.1 Sol |
| `gemini38f`, `_v2`, `_high` | 45 | Gemini 3.8 Flash variants |
| `haiku`, `opus` | 30 each | Pilot comparison runs |
| `gemini4argon_v2`, `deepseekv32`, `gptoss120b` | 15 | Small trials |

### Card structure (`card.json`)

```jsonc
{
  "schema_version": "1.0",
  "identity":   { "bibcode", "title", "year", "journal", "first_author", "n_authors",
                  "arxiv_id", "doi", "heldout", "archival_class_ours", "alma_projects_obscore" },
  "body": {
    "depth":                "full | light",
    "paper_type":           "observational_alma_primary | archival_reuse | ...",
    "paper_type_evidence":  [ ... ],
    "science":              { fields, question, targets },
    "data":                 { ALMA projects, bands, arrays, resolution, sensitivity, other facilities, external data },
    "processing":           { calibration, imaging, inherited_from_earlier_work, not_stated_but_needed },
    "analysis_steps":       [ { order, goal, method, software, fitting, validation, techniques } ],
    "software":             [ { name, version, used_for } ],
    "results_numeric":      [ { quantity, value, uncertainty, units, from_step } ],
    "findings_qualitative": [ ... ],
    "claims":               [ { hypothesis, experiment, result, finding, support } ],
    "reasoning":            { ... },
    "reproducibility":      { ... },
    "links":                { ... }
  },
  "provenance": { "model", "batch_id", "run", "collected_at", "usage", "text_source", "extractor", "text_quality" },
  "checks":     { "quotes", "quotes_ok", "quote_pass_rate", "unsupported_facts", "project_codes",
                  "codes_not_in_obscore", "numeric_problems", "fill", "evidence_ok" }
}
```

Every factual field carries a supporting **verbatim quote** and its section location. Fields the paper does not state are recorded explicitly as `_not stated_`, not guessed. That makes the cards useful for measuring *what papers leave out*, not just what they report.

### Evidence verification (`evidence_check.json`)

Each card is checked automatically against the source text:

- **Quotes** — each supporting quote must appear verbatim (after normalisation) in the paper text.
- **Unsupported facts** — facts with no matching quote are flagged.
- **ALMA project codes** — must be well-formed, appear in the paper text, and match the ALMA ObsCore archive. Codes ObsCore links to the paper but the card misses are also reported.
- **Numeric results** — values, uncertainties and units are sanity-checked.
- **Fill rate** — the fraction of schema facts the paper actually states.

A card is `evidence_ok` only when all checks pass.

---

## `catalog/` — analysis-ready tables

Parquet tables flattened from the 3,500 verified cards. All join on `bibcode`.

| File | Rows | Columns |
|---|---|---|
| `papers.parquet` | 3,500 | bibcode, title, year, journal, first_author, heldout, depth, paper_type, fields, bands, arrays, techniques, rediscovery_candidate, repro_score, fill_rate |
| `datasets.parquet` | 7,387 | bibcode, project_code |
| `software.parquet` | 14,443 | bibcode, name, version, used_for |
| `steps.parquet` | 19,136 | bibcode, order, goal, method, software, fitting, validation, techniques |
| `results.parquet` | 42,037 | bibcode, quantity, value, uncertainty, units, from_step |
| `claims.parquet` | 11,105 | bibcode, hypothesis, experiment, result, finding, support |

```python
import pandas as pd
papers   = pd.read_parquet("catalog/papers.parquet")
software = pd.read_parquet("catalog/software.parquet")

# Which papers used RADMC-3D, and what for?
software[software.name.str.contains("RADMC", case=False)].merge(papers, on="bibcode")[["bibcode", "year", "used_for"]]
```

**Paper types:** observational, ALMA primary (1,982) · archival reuse (591) · multi-facility, ALMA minor (568) · large program or survey (217) · theory/simulation compared to ALMA (110) · technical/calibration (25) · data release/catalog (7).

---

## `skills/` — technique skills

46 skills, each a folder with a `SKILL.md` (YAML front matter with `name` and `description`, then the guide), `references/sources.md` listing the papers it was built from, and a `review/` folder with an independent review and how it was reconciled. Each skill reports how many papers it rests on and warns when the evidence is thin.

| Skill | Papers | Skill | Papers |
|---|---|---|---|
| claim-verification | 3,455 | stacking | 118 |
| analysis-software-map | 3,422 | isotopic-ratios | 99 |
| paper-reproduction | 3,225 | outflow-energetics | 97 |
| imaging-choices | 2,488 | source-extraction-counts | 95 |
| archival-data-reuse | 1,764 | variability-time-domain | 90 |
| continuum-subtraction | 1,551 | core-extraction-cmf | 67 |
| moment-maps | 1,087 | line-identification | 65 |
| sed-fitting | 989 | lens-modelling | 61 |
| rotational-diagram-lte | 930 | toomre-stability | 51 |
| dust-continuum-mass | 915 | chemical-modelling | 46 |
| self-calibration | 896 | smbh-gas-dynamics | 35 |
| gas-mass-co-conversion | 876 | solar-observations | 35 |
| array-combination | 714 | transient-afterglows | 35 |
| radiative-transfer-modelling | 656 | evolved-star-envelopes | 24 |
| spectral-index | 640 | absorption-lines | 18 |
| uv-plane-fitting | 638 | sz-effect | 14 |
| keplerian-disk-kinematics | 447 | disk-substructure-profiles | — |
| star-formation-laws | 414 | envelope-kinematics-pv | — |
| non-lte-excitation | 370 | hydro-simulation-comparison | — |
| redshift-line-search | 368 | solar-system-atmospheres | — |
| free-free-synchrotron | 341 | | |
| galaxy-3d-kinematics | 341 | | |
| injection-null-tests | 208 | | |
| dense-gas-tracers | 180 | | |
| gmc-decomposition-virial | 127 | | |
| polarization-magnetic-fields | 109 | | |

Supporting files in `skills/`:

- `index.json` — index of techniques, skills, review status and packs.
- `packs/` — per-skill evidence packs: `<skill>.md` (the card excerpts the skill was written from) and `<skill>.bibcodes.json`.
- `stats/` — corpus-wide CSVs: software overall / by year / by field, settings, unstated-detail rates, and the tools gap. See `stats/README.md`.
- `task_seeds/` — seed tasks derived from the corpus.
- `tools_gap.md` — software ALMA papers rely on, ranked by usage, versus what the Quasar agent can already call.

The skills follow the Agent Skills format (`SKILL.md` with front matter), so a skill folder can be dropped into a Claude Code or Claude Agent SDK skills directory.

---

## Other folders

- **`batches/`** — 110 JSONL request files for the Anthropic Message Batches API, named `<run>_<model>_<kind>_<timestamp>_<part>.jsonl`, where kind is `card`, `figures` or `repair`. Each request holds the system rules, the card JSON schema and the full paper text.
- **`selections/`** — bibcode lists for each production run, e.g. `sonnet_run1_1000.txt` (1,000 papers, LaTeX-extracted, good quality first, seeded shuffle) and `sonnet_run2.txt` (3,961 papers).
- **`pilot/`** — the model-selection pilot: `pilot.tsv` (pilot paper list, including held-out benchmarks), `compare.json` (Haiku vs Sonnet vs Opus card comparison), `estimate.json` (cost projection), `review_sheet.html`, and `smoke/` test cards.
- **`sources/`** — raw upstream metadata: `ads/` (ADS query snapshot `20261027T094643434994Z`), `arxiv_api/` (arXiv API batch responses) and `obscore/` (bibcode-to-project map from the ALMA ObsCore TAP service at `almascience.nrao.edu/tap`, used to cross-check project codes).
- **`logs/`** — stdout and JSON logs from download, extraction, card runs (Sonnet, Gemini Argon, Codex, TACC), skill rebuilds and the progress dashboard.

### Excluded folders (local only)

- **`raw/<xx>/<bibcode>/`** — `meta.json`, `paper.pdf` and, where available, `source.tar.gz` (arXiv LaTeX source). Sharded into 256 folders by hash prefix. ~50 GB, 14,990 files.
- **`text/<bibcode>/`** — `fulltext.md` (extracted text with section markers), `pages.json`, `pdf_text.json` and `figures/` (PNG figures plus `figures.json` captions). ~9.8 GB, 75,374 files.

---

## How the corpus was built

1. **Select** — query NASA ADS for refereed papers that use ALMA data; join with the ALMA ObsCore archive to attach project codes and classify each paper as PI, archival or both.
2. **Fetch** — download the open-access copy for each paper, preferring arXiv LaTeX source, then Unpaywall and publisher PDFs. Every request is logged in `fetches`.
3. **Extract** — convert LaTeX (or PDF as a fallback) to clean Markdown with section markers, page maps and figures, and grade extraction quality.
4. **Card** — send each paper with the card schema and rules to an LLM (mostly Claude Sonnet 5.5 through the Batch API). A model-comparison pilot chose the production model.
5. **Verify** — check every quote, project code and number against the source text and ObsCore. Cards that fail get a repair pass.
6. **Catalog** — flatten verified, non-held-out cards into Parquet tables.
7. **Skills** — group cards by technique, write a skill per technique from the evidence pack, have it reviewed independently, and reconcile the review.

The pipeline code (`scripts/alma_corpus`: `download`, `extract`, `shred`, `verify`, `repair`, `skills`, `dashboard`, …) lives in the separate Quasar project and is not included here. The skill statistics, for example, were generated with `python -m scripts.alma_corpus skills --stats`.

### Held-out papers

17 papers are marked `heldout = 1` as a benchmark for paper reproduction. They are excluded from the skill packs and corpus statistics, so the skills can be evaluated on them without leakage. Two of them appear in `catalog/papers.parquet` with `heldout = True`; filter on that column when building training data.

---

## Copyright and licensing

The cards, catalog, skills and statistics are derived works produced by this project. **The underlying papers remain the copyright of their authors and publishers.** Each paper's licence, as reported by arXiv or the publisher, is recorded in `manifest.sqlite` (`papers.license`):

| Licence | Papers |
|---|---|
| arXiv non-exclusive distribution licence | 3,362 |
| CC BY 4.0 | 1,310 |
| CC BY-NC-ND 4.0 | 110 |
| CC BY-NC-SA 4.0 | 94 |
| CC0 / public domain | 37 |
| CC BY-SA 4.0 | 25 |
| Unknown | 234 |

Some files in this repository — the requests in `batches/` and the `prompt.md` / `repair_prompt.md` files in `cards/` — contain the full extracted text of the papers. Anyone reusing those files should respect each paper's licence. Cards quote short verbatim passages as supporting evidence.

ALMA is a partnership of ESO, NSF (USA) and NINS (Japan), together with NRC (Canada), NSTC and ASIAA (Taiwan) and KASI (Republic of Korea), in cooperation with the Republic of Chile. This research has made use of NASA's Astrophysics Data System and the arXiv e-print service.

---

## Citation

If you use this corpus, please cite this repository:

```
Anil, A. Z. (2026). ALMA Corpus: evidence-checked methods cards and technique skills
from 5,173 ALMA papers. https://github.com/adamzacharia/alma-corpus
```
