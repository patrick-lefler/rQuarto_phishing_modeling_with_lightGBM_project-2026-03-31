# Infrastructure-Based, Machine-Learning Phishing Detection

> Proactive phishing defense using URL infrastructure fingerprints, LightGBM gradient boosting, and the tidymodels ecosystem in R.

**Author:** Patrick Lefler

**Published:** March 31, 2026

**Rendered:** https://patrick-lefler.github.io/rQuarto_phishing_modeling_with_lightGBM_project-2026-03-31/

---

## Project Introduction

> Shifts phishing detection from reactive block-listing to proactive risk-patterning by analyzing 41 URL infrastructure features — including character entropy, subdomain depth, and path complexity — using a LightGBM model trained on 247,950 labeled URLs.

---

## Overview

This project trains a LightGBM classifier via the `bonsai` engine inside R's `tidymodels` framework to identify phishing URLs based on structural infrastructure signals rather than email content or static block lists. The dataset, sourced from Mendeley Data, contains 247,950 instances across 41 engineered features. The model is evaluated under two distinct security postures: a secure-first stance optimized for maximum recall (99.2%), and a user-centric stance that minimizes false positives to reduce operational friction. Variable Importance Plots generated with the `vip` library provide an explainable audit trail, translating the gradient-boosting black box into actionable intelligence for risk stakeholders.

---

## Tech Stack

- **Language:** R
- **Framework:** [Quarto](https://quarto.org/)
- **Primary Libraries:** tidymodels, lightgbm, bonsai, probably, vip, ggplot2, kableExtra, plotly
- **Deployment / Output:** Rendered HTML Document (self-contained)

---

## Repository Structure

```
├── data/               # Raw phishing dataset (mendeley_phishing_dataset.csv)
├── scripts/            # Helper R scripts
├── models/             # Saved model objects (.rds)
├── output/             # Rendered HTML files
├── _brand.yml          # Brand configuration
└── index.qmd           # Main Quarto entry point
```

---

## Key Findings

**URL infrastructure outperforms content analysis as a phishing signal.** The top predictors — URL entropy, subdomain depth, and total path length — are structural properties that remain stable even when attackers rotate email copy or spoof brand logos. This makes the model resilient to surface-level evasion tactics.

**The model achieves a 99.2% detection rate (Recall) at the secure stance**, with a ROC AUC of 0.963. At the user-centric threshold, precision holds at 94.5% — meaning fewer than 6 in 100 flagged URLs are false positives, keeping SOC workloads manageable.

**Phishers are actively mimicking legitimate cloud infrastructure.** The LightGBM engine identified that attackers increasingly replicate the directory depth patterns of services like AWS and Azure. Traditional signature-based filters miss this pattern entirely; the model does not.

---

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## Contact

Patrick Lefler — [LinkedIn](https://www.linkedin.com/in/patricklefler/) | [Website](https://patrick-lefler.github.io) | [Substack](https://substack.com/@pflefler)
