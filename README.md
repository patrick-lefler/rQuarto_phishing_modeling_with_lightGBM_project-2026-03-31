# Infrastructure-Based, Machine-Learning Phishing Detection

**Author:** Patrick Lefler  
**Published:** 2026-03-31  
**Tools:** R | Quarto |  | ggplot2 | kableExtra

---

## Overview

[abstract goes here]

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

This is Project 1 in a planned three-part series on Bayesian position sizing:

- **Project 1 (this document):** Bayesian Kelly under single-asset uncertainty
- **Project 2 (planned):** Multi-asset Kelly — portfolio allocation with correlated returns
- **Project 3 (planned):** Regime-aware Kelly — GARCH-EVT volatility regimes and tail-adjusted sizing

---

## License

MIT License. You are free to use, adapt, and republish this analysis with attribution.
