# PubChat Supplementary Materials

This repository contains the supplementary materials for the manuscript:

**PubChat: An Autonomous AI Agent for Zero-Hallucination Biomedical Literature Retrieval and Evidence-Based Hypothesis Generation**

---

## Background

Citation hallucination remains a widespread problem in LLM-assisted literature retrieval. PubChat addresses this by anchoring all retrieval to the PubMed E-utilities API and restricting LLMs to multi-tier semantic relevance scoring — converting LLMs from unreliable knowledge oracles into verifiable expert librarians.

PubChat was validated against 20 Cochrane systematic reviews (585 ground-truth articles) across eight languages, outperforming four general LLMs (GPT-5.2-Thinking, Gemini-3.0-Pro, Grok-4.1-Thinking, and Qwen3-Max), one search-augmented retrieval tool (Perplexity-Sonar), and three specialized retrieval tools (Elicit, ASTA, and Consensus), achieving a Pareto-optimal position in Precision–Recall space with zero citation hallucinations.

The standalone **Micro-Innovation Discovery Engine (MIDE)** was developed as a companion tool to convert high-recall corpora into structured, evidence-traceable research gaps and frontier hypotheses.

---

## Open-Source Code

| Tool | Repository |
|------|-----------|
| PubChat | https://github.com/PubChatOfficial/PubChat_smart_literature_search |
| MIDE | https://github.com/PubChatOfficial/MIDE-skill |

---

## Repository Contents

### Supplementary Material 1 — PubChat 8-Language Retrieval Output for 20 CDSR Reviews

- `1.1 Benchmark Definitions for 20 CDSR Reviews.xlsx` — Ground-truth benchmark definitions for all 20 Cochrane systematic reviews
- `1.2.01` – `1.2.20` — Per-CDSR PubChat retrieval outputs across 8 languages (Chinese, English, French, German, Italian, Portuguese, Russian, Spanish)

### Supplementary Material 2 — PubChat vs 8-Tool Benchmarking Data with Evaluation Protocols

- `2.1 PubChat vs 8-Tool Benchmarking Raw Data.xlsx` — Sheet S1: Retrieval Results (4,935 rows); Sheet S2: JCR Metrics (18,206 rows)
- `2.2 Tool Evaluation Protocols and Prompt Template.docx` — Standardized evaluation protocols and prompt templates used across all tools

### Supplementary Material 3 — PubChat User Survey: 42-Item Questionnaire (PDF)

User evaluation instrument administered to 279 biomedical researchers from 18 countries, covering reliability, innovation, efficiency, user experience, and preference (28 Rasch-validated Likert-scale items).

### Supplementary Material 4 — MIDE Case Study: Periodontitis and CKD

- `4.1 MIDE workflow and configuration.docx` — Detailed MIDE pipeline description and configuration parameters
- `4.2 PubChat-Generated Periodontitis-CKD Corpus with MIDE Novelty Scores.xlsx` — Sheet 1: Full Corpus (490 articles); Sheet 2: Discovery Pool (112 articles); Sheet 3: MIDE Configuration
- `4.3 MIDE Mini-Review Output - 10 Frontier Research Directions.pdf` — Structured mini-review linking established knowledge to frontier hypotheses across the periodontitis–CKD axis

---

## Contact

For questions regarding the supplementary materials or to request access to additional data, please contact the corresponding authors.
