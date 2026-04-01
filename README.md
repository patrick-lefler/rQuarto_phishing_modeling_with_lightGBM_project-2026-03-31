# Infrastructure-Based, Machine-Learning Phishing Detection

**Author:** Patrick Lefler  
**Published:** 2026-03-31  
**Project #:** 11 </br>
**Tools:** R | Quarto |  | ggplot2 | kableExtra

---

## Overview

This project sets up a proactive defense against phishing. It shifts the focus from temporary email content to the digital fingerprints of URLs. The project utilizes a robust dataset with 41 unique features. These include character entropy, subdomain depth, and path complexity. This approach goes beyond just using a simple block list. It aims to identify the core patterns of malicious intent in a domain’s setup. </br> 

The `lightGBM` (Light Gradient Boosting Machine) package is utilized with the <code>bonsai</code> engine in R's `tidymodels` ecosystem. This helps manage complex data at scale. `LightGBM` was chosen for its leaf-wise tree growth strategy. This method is great at spotting subtle, non-linear connections between URL features, that traditional models often miss. It also offers the efficiency needed for real-time network log analysis. </br> 

The resulting model gives a clear and adjustable security posture. The R `probably` library is used to switch between two models. The secure-first stance aims to catch nearly all threats. The user-centric stance focuses on reducing false positives, which helps boost productivity. </br> 

Additionally, Variable Importance Plots (VIP) are employed using the R `vip` library for transparency. This turns the machine learning black box into a clear audit trail. Readers can spot indicators that influence risk scores. These include high URL entropy and strange directory structures. This makes sure defensive choices are based on data and match an organization's risk tolerance.

---

## Key insights

**Infrastructure-First Detection**
Traditional phishing filters often rely on "blacklists" of known bad domains or keywords in an email. This project proves that URL Infrastructure (how a web address is built) is a more stable and reliable signal. By analyzing 41 "digital fingerprints," we can identify a malicious site even if it has never been reported before, effectively stopping "Zero-Day" attacks at the perimeter.

**High-Confidence Risk Posture (99.2% Recall)**
In cybersecurity, missing one attack is far more costly than a false alarm. This project successfully optimized a "Secure-First" stance, achieving a 99.2% Recall rate. This means the model captures nearly every phishing attempt in the dataset, providing a robust safety net for an organization’s most vulnerable entry point: the user's browser.

**Transparency via Feature Importance**
Machine learning is often criticized for being a "black box," but this project prioritizes Explainable AI. Using Variable Importance Plots, we identified exactly which traits—such as URL Randomness (Entropy) and Subdomain Complexity—drive the risk score. This transparency allows risk stakeholders to understand the "Why" behind every block, creating a defensible and auditable security process.

**Strategic Efficiency with LightGBM**
By using the LightGBM algorithm, this project demonstrates that enterprise-level security doesn't require massive computing power. The model is "Light" enough to process hundreds of thousands of network logs in seconds while remaining sophisticated enough to detect non-linear patterns that simpler models would miss. This makes it a scalable solution for real-time traffic monitoring.

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
