# SAICRED v2 — Benchmark Results Dashboard

**Standard for Assessing AI for Catholic Reliability and Doctrinal Fidelity**
Version 2.0 · April 2026 · Dr. Filip Ponulak, Project Lead

---

## Overview

This repository provides an interactive HTML dashboard for visualizing the SAICRED v2 benchmark results. The underlying data was produced by the SAICRED engineering pipeline and published to Google Drive by the lead engineer. Because the original GitHub repository link did not resolve to accessible results, this dashboard was built directly from the CSV files shared via Google Drive to make the findings navigable and readable for the project team and institutional stakeholders.

No data was modified. All scores, rankings, and findings in this dashboard reflect the raw pipeline output exactly as delivered.

---

## What SAICRED Measures

SAICRED evaluates how faithfully leading AI models represent Catholic doctrine across real-world use cases. The v2 benchmark tested six general-purpose models against 100 doctrinal questions presented in four framing variants — neutral, Christian, Catholic, and adversarial — producing 400 prompts, 2,400 model responses, and 21,268 metric scores.

Each response is scored across nine metrics and assigned a Catholic Doctrinal Fidelity Index (CDFI) composite score. The CDFI determines a deployment tier recommendation for each response.

---

## Models Tested

| Model | Developer |
|-------|-----------|
| o3 | OpenAI |
| Gemini 3.1 Pro | Google |
| GPT-5.4 | OpenAI |
| DeepSeek V4 | DeepSeek |
| Grok 4 | xAI |
| Claude Sonnet 4.6 | Anthropic |

---

## Evaluation Metrics

| Metric | Type | Description |
|--------|------|-------------|
| Doctrinal Precision | 0–5 | Response includes all required doctrinal elements |
| Moral Fidelity | 0–5 | Moral norms stated with full authoritative weight |
| Hallucination | Pass/Fail | All cited sources are real and verifiable |
| Confidence Calibration | 0–5 | Expressed certainty matches actual doctrinal authority |
| Relativism Resistance | Pass/Fail | No false equivalence between Catholic teaching and other positions |
| Source Citation | 0–5 | Magisterial sources referenced appropriately |
| Completeness | 0–5 | All major doctrinal dimensions addressed |
| Pastoral Appropriateness | 0–5 | Tone is charitable, clear, and directs to clergy when warranted |
| Stability | 0–5 | Consistent responses across repeated prompts |

---

## CDFI Deployment Tiers

| Score | Tier |
|-------|------|
| 85 and above | Approved — formation and catechesis |
| 70 – 84 | Approved — general information use |
| 50 – 69 | Research and development only |
| Below 50 | Not recommended |

A hard-fail cap applies: any response that fails the hallucination or relativism resistance gate is capped at 40 regardless of other metric scores.

---

## Headline Finding

All six models cleared the 70-point general information threshold. None cleared 85 for formation and catechesis. No current general-purpose AI model is cleared for catechetical or spiritual formation use without human theological oversight.

o3 came closest at an average CDFI of 84.9 — 0.1 points below the formation threshold.

---

## Dashboard Pages

| Page | What It Shows |
|------|---------------|
| Overview | Model rankings, average CDFI scores, deployment tier summary |
| Model Rankings | Detailed table with mean, median, standard deviation, cap rates, and tier distribution |
| Metric Heatmap | Color-coded grid of average scores per model per metric |
| Failure Explorer | Pass/fail rates for hallucination and relativism resistance; hard-fail cap rate by model |
| Variant Analysis | CDFI by framing variant — reveals framing sensitivity across models |
| Topic Analysis | Field-average CDFI by doctrinal domain — identifies where all models struggle |
| CDFI Distribution | Score band distribution showing the bimodal nature of results |
| Raw Data | Filterable tables by model, metric, variant, topic, and cap events |

---

## How to Use

Download `index.html` and open it in any modern browser. No server, no database, no dependencies to install. Chart.js loads from CDN. All data is embedded in the file.

To host on GitHub Pages: upload `index.html` to a public repository, enable Pages under Settings → Pages, and deploy from the main branch root.

---

## Data Source

All benchmark data originates from the SAICRED v2 evaluation pipeline built and executed by the lead engineer. Source files:

- `prompts_full.csv` — 400 prompts with ground truth, scoring anchors, and doctrinal metadata
- `responses_full.csv` — 2,400 model responses with full metadata
- `scores_full.csv` — 21,268 metric scores with judge reasoning
- `cdfi_scores_full.csv` — CDFI composite scores with deployment tier assignments

LLM judge: Gemini 2.5 Flash. Evaluation method: LLM-as-judge across 8 metrics; stability hardcoded at 3.0 pending multi-run evaluation pass.

---

## Methodology Note

The current rankings are preliminary in two respects. First, all 400 prompts defaulted to `ordinary_magisterium` in the CDFI weighting matrix because authority-level classification was not completed prior to the evaluation run. The full four-column weighted CDFI — which differentiates defined dogma, ordinary magisterium, theological consensus, and legitimate theological opinion — has not yet been computed. Second, rankings are point estimates without confidence intervals. Both items are documented as next steps before publication.

---

## Project

SAICRED is an open-source Catholic AI benchmark led by Dr. Filip Ponulak and released under the Catholic Digital Commons Foundation.

White paper: [SAICRED — Standard for Assessing AI for Catholic Reliability and Doctrinal Fidelity](https://docs.google.com/document/d/1VvGeY_T56KNvOaY3n2GAsNSr4AqEgfVgRh5vmadRawg/edit?usp=sharing)

