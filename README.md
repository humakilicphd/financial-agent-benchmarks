# 📊 Financial LLM Benchmark Datasets

A collection of **four benchmark datasets** — three built on independent data sources plus one hybrid cross-source dataset — for evaluating large language models on financial reasoning and interpretation tasks in the Turkish capital markets domain.

Each single-source dataset targets a distinct data source and question type, with **question–answer pairs derived through a rule-based + LLM-assisted pipeline**, followed by **domain-expert human verification**. The Hybrid RAG dataset builds on top of these three to test cross-source reasoning.

---

## 📁 Datasets

### 📰 KAP — Public Disclosure Platform Dataset
> *Kamuyu Aydınlatma Platformu (KAP)*

- **Source:** Financial reports (FR), material event disclosures (ODA), and other mandatory filings published on KAP for **BIST-30** constituents, covering **February–May 2026**
- **Question categories (balanced distribution across 5 categories):**
  - 💰 Financial performance
  - 💵 Dividends
  - 🏦 Debt structure
  - ⚙️ Operational indicators
  - 🌍 International operations
- **Gold answers:** Strictly limited to figures and statements explicitly stated in the source documents

### 🐦 Twitter/X — Sentiment Metrics Dataset
> *Social media sentiment signals*

- **Source:** Weekly sentiment metrics for **BIST-30** constituents, computed from Twitter/X data
- **Metrics used:**
  - **P** — Positive sentiment score
  - **N** — Negative sentiment score
  - **E** — Engagement/impact score
  - **L** — Like rate
  - **R** — Retweet rate
- **Sentiment labeling:** Derived **deterministically** via rule-based threshold values applied to the P/N ratio
- **Gold answers:** Grounded directly in the extracted sentiment metrics, not interpretive judgments

### 📈 PRICE — BIST Price Movement Dataset
> *Borsa İstanbul (BIST) price action signals*

- **Source:** Time-series queries based on **weekly closing prices**, starting from **06.07.2024**, via the MCP-Price tool
- **Focus:** Question–answer pairs on numerical price behavior within defined time windows
- **Gold answers:** Based purely on the underlying numerical price data

### 🔀 Hybrid RAG — Cross-Source Dataset
> *Unified context from all three sources*

- **Source:** Combined context drawn jointly from **KAP disclosures**, **Twitter/X sentiment metrics**, and **BIST price data**
- **Focus:** Question–answer pairs that require reasoning across multiple data sources simultaneously, testing a model's ability to synthesize disclosure information, market sentiment, and price behavior into a single, grounded answer
- **Gold answers:** Derived from the merged multi-source context, remaining strictly limited to what is explicitly present across the combined sources

---

## 🧩 Construction Methodology

| Step | Description |
|---|---|
| 🔍 **Extraction** | Q&A pairs derived from source documents using a rule-based + LLM-assisted process |
| 🎯 **Gold answer scope** | Limited strictly to figures and statements directly present in the source — **no inference, commentary, or prediction included** |
| ✅ **Human verification** | Each of the three datasets was independently reviewed and validated by **domain experts** |

> ⚠️ **Note:** Gold answers deliberately exclude interpretive, speculative, or forward-looking statements. They reflect *only* what is explicitly present in the source data — the datasets are designed to test grounded, data-faithful reasoning rather than open-ended financial commentary.

---

## 🗂️ Repository Structure

```
.
├── kap/         # KAP disclosure dataset
├── twitter/     # Twitter/X sentiment dataset
├── price/       # BIST price movement dataset
├── hybrid-rag/  # Cross-source (KAP + Twitter/X + PRICE) dataset
└── README.md
```

*(Update paths/format above to match your actual repo layout.)*

---

## 📄 License

<!-- Add license info here, e.g. MIT, CC-BY-4.0 -->

## 📌 Citation

If you use these datasets in your work, please cite this repository.
