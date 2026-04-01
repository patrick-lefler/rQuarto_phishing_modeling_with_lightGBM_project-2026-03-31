# Infrastructure-Based, Machine-Learning Phishing Detection

**Author:** Patrick Lefler  
**Published:** 2026-03-31  
**Project #:** 11 </br>
**Tools:** R | Quarto |  | ggplot2 | kableExtra

---

## Overview

This project sets up a proactive defense against phishing. It shifts the focus from temporary email content to the digital fingerprints of URLs. The project utilizes a robust dataset with 41 unique features. These include character entropy, subdomain depth, and path complexity. This approach goes beyond just using a simple block list. It aims to identify the core patterns of malicious intent in a domain’s setup. </br> </br>

The `lightGBM` (Light Gradient Boosting Machine) package is utilized with the <code>bonsai</code> engine in R's `tidymodels` ecosystem. This helps manage complex data at scale. `LightGBM` was chosen for its leaf-wise tree growth strategy. This method is great at spotting subtle, non-linear connections between URL features, that traditional models often miss. It also offers the efficiency needed for real-time network log analysis. </br> </br>

The resulting model gives a clear and adjustable security posture. The R `probably` library is used to switch between two models. The secure-first stance aims to catch nearly all threats. The user-centric stance focuses on reducing false positives, which helps boost productivity. </br> </br>

Additionally, Variable Importance Plots (VIP) are employed using the R `vip` library for transparency. This turns the machine learning black box into a clear audit trail. Readers can spot indicators that influence risk scores. These include high URL entropy and strange directory structures. This makes sure defensive choices are based on data and match an organization's risk tolerance.

---

## Key concepts

**Bayesian updating** — Prior beliefs about the win probability are updated using observed wins and losses via Bayes' theorem. For a Binomial likelihood with a Beta prior, the posterior is analytically tractable: Beta(α + wins, β + losses).

**Kelly fraction distribution** — Rather than computing a single Kelly recommendation, 10,000 values of the win probability are drawn from the posterior. Each produces a Kelly fraction. The resulting distribution reveals the full range of defensible stakes given the available evidence.

**Percentile-based staking** — The p25 Kelly fraction — the stake that is optimal if the true win rate is anywhere in the upper 75% of the uncertainty range — is proposed as the recommended default. The gap between p25 and p50 (the overconfidence premium) quantifies the cost of treating an estimated probability as a known one.

**Scenario 4: Optimism meets reality** — The most important scenario in the document. Identical inputs to Scenario 1, but the wealth simulation uses a true win rate of 52% rather than the posterior mean of 56.3%. This is the out-of-sample test: full Kelly degrades badly; the p25 stake survives.

---

## Repository structure

```
rQuarto_phishing_model_with_lightGBM/
├── index.qmd                  # Main Quarto document
├── _brand.yml                 # Brand colours and typography
├── _quarto.yml                  
├── README.md                  # This file
└── docs/                        
    └── index.html             # Rendered HTML output (GitHub Pages)
└──  data
    └──  mendeley_phishing_dataset.csv  # Downloaded data

```

---

## Reproducing the analysis

### Prerequisites

R 4.3 or later with the following packages:

```r
library(bonsai)
library(forcats)
library(ggplot2)
library(knitr)
library(kableExtra)
library(lightgbm)
library(plotly)
library(probably)
library(scales)
library(sessioninfo)
library(tidyverse)
library(tidymodels)
library(tidyr)
library(vip)
library(dplyr)
```

Quarto 1.4 or later. Install from [quarto.org](https://quarto.org).

## Design standards

- **Theme:** Quarto Sandstone (Bootswatch)
- **Brand:** Custom palette defined in `_brand.yml` — off-white background, dark grey text, blue/red/green accent ramps
- **Typography:** Roboto (Google Fonts, via `_brand.yml`)
- **Visualizations:** `ggplotly()` for density overlays, `plot_ly()` / `add_bars()` for Kelly histograms and trajectory panels
- **Tables:** `kbl()` + `kable_styling()` with striped, hover, condensed, responsive bootstrap options
- **No Shiny, no OJS** — document renders to a standalone HTML file that works from the filesystem or any web host

## Related projects

None

---

## License

MIT License. You are free to use, adapt, and republish this analysis with attribution.
