# Causal Meta-Analysis — Simulation

Code accompanying the paper **"Causal Meta-Analysis: Rethinking the Foundations of Evidence-Based Medicine"** (Berenfeld, Boughdiri, Colnet, van Amsterdam, Bellet, Khellaf, Scornet, Josse).

📄 Paper: https://arxiv.org/abs/2505.20168

## What this does

The paper shows that classical fixed-effects (FE) and random-effects (RE) meta-analysis estimators only admit a clean causal interpretation for the **risk difference**, and that this breaks down for non-linear measures such as the **risk ratio** and **odds ratio**. It introduces causal aggregation formulas that work directly from aggregated (contingency-table) data, without requiring individual-level data.

This repository runs the analysis over a large collection of **real published meta-analyses**, comparing the classical random-effects estimator against the causal estimator (`θ_causal`) for the three common contrasts — risk difference (RD), risk ratio (RR), and odds ratio (OR). It reproduces the empirical results of Section 5: the two methods usually agree, but the code surfaces the outlier cases where conclusions diverge — including cases where a treatment looks beneficial under a classical analysis yet is harmful under the causal lens.

## Files

- `Simulation.Rmd` — R Markdown notebook that loads the meta-analysis dataset, computes the random-effects and causal estimators (RD, RR, OR) for each meta-analysis, and produces the comparison plots and summary statistics (discrepancy, CI lengths, CI overlap).
- `out2_ma_sample_2.csv` — the input dataset: a large collection of real published meta-analyses (per-study contingency-table counts), drawn from the Cochrane Library, that the code runs on.

## Running

Open `Simulation.Rmd` in RStudio and knit it, or from R:

```r
rmarkdown::render("Simulation.Rmd")
```

Typical dependencies: `metafor` (classical random-effects fitting), plus standard data/plotting packages (`ggplot2`, `dplyr`). The causal estimators can also be computed with the companion package:

```r
install.packages("CaMeA")  # Causal Meta-Analysis on Aggregated data (CRAN)
```

## Citation

```bibtex
@article{berenfeld2025causal,
  title  = {Causal Meta-Analysis: Rethinking the Foundations of Evidence-Based Medicine},
  author = {Berenfeld, Cl{\'e}ment and Boughdiri, Ahmed and Colnet, B{\'e}n{\'e}dicte
            and van Amsterdam, Wouter and Bellet, Aur{\'e}lien and Khellaf, R{\'e}mi
            and Scornet, Erwan and Josse, Julie},
  journal = {arXiv preprint arXiv:2505.20168},
  year    = {2025}
}
```
