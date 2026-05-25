[![arXiv](https://img.shields.io/badge/arXiv-2603.04083-b31b1b.svg)](http://arxiv.org/abs/2603.04083)
[![LREC 2026](https://img.shields.io/badge/LREC-2026-blue.svg)](https://lrec.elra.info/lrec2026-main-688)



# HINDEX — Hindsight Quality Prediction Experiments in Machine Translation

<img src="hindex_logo.png" alt="Hindex promo" width="180" align="left">

This is the companion repository to *“Hindsight Quality Prediction Experiments in Multi-Candidate Human-Post-Edited Machine Translation”* (Marmonier et al., 2026). This paper investigates how machine translation quality-prediction paradigms — **source-side translation difficulty prediction** and **candidate-side quality estimation (QE)** — behave across different machine translation (MT) architectures. We use a multi-candidate, human post-edited dataset and "hindsight" experiments to quantify the predictive strength of various metrics and heuristics using Kendall's $\tau$.

This repository lets you **reproduce the results from the paper**:
- Source-side difficulty metrics vs. translation quality (TER, COMET, ChrF)
- Candidate-side QE correlations (COMET-QE, MetricX-QE) across NMT and LLM systems
- Positional bias in document-level MT

---

## 🗂️ What this repository contains

- **`Hindex_Notebook.ipynb`** — the main notebook.  
  It reproduces all core analyses and heatmaps:
  - *Source-side difficulty prediction*: Readability, surprisal, and neural predictors vs. final COMET / TER / CHRF.  
  - *Candidate-side quality estimation*: COMET-QE / MetricX-QE correlations across NMT and LLM systems.  
  - *Positional bias*: Tests whether translation quality drifts over long-context sequences.
- **`data/`** — Pre-processed data files.
  - Contains over 6,000 English source segments and their final French post-edited references.
  - Includes translation hypotheses and pre-computed metric scores for 9 distinct systems (including Llama 4, DeepSeek-R1, MADLAD-400, and NLLB).
---

## 💻 How to Run

You can run the notebook on **Google Colab**:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/mmarmonier/Hindex/blob/main/Hindex_Notebook.ipynb)
---

## 📜 Citations
If you use this code or dataset, please cite:
```
@inproceedings{marmonier-etal-2026-hindsight,
  title = {Hindsight Quality Prediction Experiments in Multi-Candidate Human-Post-Edited Machine Translation},
  author = {Marmonier, Malik and Sagot, Benoît and Bawden, Rachel},
  booktitle = {Proceedings of the Fifteenth Language Resources and Evaluation Conference (LREC 2026)},
  month = {May},
  year = {2026},
  pages = {8740--8755},
  address = {Palma, Mallorca, Spain},
  publisher = {European Language Resources Association (ELRA)},
  editor = {Piperidis, Stelios and Bel, Núria and van den Heuvel, Henk and Ide, Nancy and Krek, Simon and Toral, Antonio},
  doi = {10.63317/24puen8nstzh},
  abstract = {This paper investigates two complementary paradigms for predicting machine translation quality: source-side difficulty prediction and candidate-side quality estimation (QE). The rapid adoption of Large Language Models (LLMs) into machine translation (MT) workflows is reshaping the research landscape, yet its impact on established quality prediction paradigms remains underexplored. We study this issue through a series of "hindsight" experiments on a unique, multi-candidate dataset resulting from a genuine machine translation post-editing (MTPE) project. The dataset consists of over 6,000 English source segments with nine translation hypotheses from a diverse set of traditional neural MT systems and advanced LLMs, all evaluated against a single, final human post-edited reference. Using Kendall’s rank correlation, we assess the predictive power of source-side difficulty metrics, candidate-side QE models and position heuristics against two gold-standard scores: TER (as a proxy for post-editing effort) and COMET (as a proxy for human judgment). Our analysis yields three primary findings: (1) On the source side, the predictive power of difficulty metrics is highly contingent on the reference metric used; features that strongly correlate with COMET (e.g., segment length, neural predictors) show much weaker correlation to TER. (2) On the candidate side, we find a significant mismatch between QE model rankings and final human-adjudicated quality, and further show that modern QE metrics are significantly more aligned with the quality of traditional neural MT outputs than with those from general-purpose LLMs. (3) While we confirm a statistically significant positional bias in document-level LLMs (i.e., the tendency for translation quality to degrade for segments occurring later in a document) its practical impact on translation quality appears to be negligible. These findings highlight that the architectural shift towards LLMs alters the reliability of established quality prediction methods while simultaneously mitigating previous challenges in document-level translation.}
}
```
and:
```
@inproceedings{marmonier-etal-2025-french,
    title = "A {F}rench Version of the {OLDI} Seed Corpus",
    author = "Marmonier, Malik  and
      Sagot, Beno{\^i}t  and
      Bawden, Rachel",
    editor = "Haddow, Barry  and
      Kocmi, Tom  and
      Koehn, Philipp  and
      Monz, Christof",
    booktitle = "Proceedings of the Tenth Conference on Machine Translation",
    month = nov,
    year = "2025",
    address = "Suzhou, China",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2025.wmt-1.80/",
    doi = "10.18653/v1/2025.wmt-1.80",
    pages = "1048--1060",
    ISBN = "979-8-89176-341-8",
    abstract = "We present the first French partition of the OLDI Seed Corpus, our submission to the WMT 2025 Open Language Data Initiative (OLDI) shared task. We detail its creation process, which involved using multiple machine translation systems and a custom-built interface for post-editing by qualified native speakers. We also highlight the unique translation challenges presented by the source data, which combines highly technical, encyclopedic terminology with the stylistic irregularities characteristic of user-generated content taken from Wikipedia. This French corpus is not an end in itself, but is intended as a crucial pivot resource to facilitate the collection of parallel corpora for the under-resourced regional languages of France."
}
```
