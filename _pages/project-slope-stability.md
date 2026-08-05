---
layout: archive
title: "Physically Admissible Slope-Stability Prediction Using Bayesian Physics-Informed Neural Networks"
permalink: /research-projects/slope-stability/
author_profile: true
---

[← Back to Research Projects](/n.hasnat_ce/research-projects/)

---

## Research in Brief

This research develops a hard-monotone Bayesian physics-informed neural network (B-PINN) for slope stability classification that guarantees physical admissibility by construction. Unlike conventional machine-learning approaches that optimize for accuracy alone, this model enforces monotonicity with respect to key geotechnical parameters — height, slope angle, pore-pressure ratio, cohesion, and friction angle — architecturally, so that every posterior draw respects the underlying mechanics.

The network is pre-trained on 2,000 finite-element simulations sampled from a 2,707-case pool generated in PLAXIS 2D and fine-tuned on 275 de-duplicated and audited field case histories. Tuned classical baselines (Random Forest, SVM, ANN, BNN) achieve higher cross-validation accuracy than the B-PINN, but McNemar's exact test cannot separate any of the fifteen model pairs at the 5% significance level, and a König/min-cut bound shows that label conflicts within the database cap any monotone classifier at 0.946. The study demonstrates that accuracy cannot discriminate among these models — but physical consistency can: every baseline violates monotonicity, while the B-PINN records zero violations, including outside its training range.

**Research Period:** 2025 – Present &nbsp;|&nbsp; **Status:** Manuscript in Preparation

---

## Key Findings

- The B-PINN achieves **zero monotonicity violations** across all parameter responses, while conventional baselines violate monotonicity in **19–31%** of out-of-range parameter sweeps
- McNemar's exact test separates **none of the 15 model pairs** at the 5% level — accuracy alone cannot discriminate among the models
- A König/min-cut bound reveals that label conflicts in the database cap any monotone classifier at **0.946 accuracy**
- SHAP analysis of the unconstrained BNN shows it assigns **lower failure probability to higher pore pressure** (Spearman ρ = −0.90), a physically inadmissible pattern
- In an 88,200-point design chart, the unconstrained network predicts decreasing failure probability with increasing slope height across **46% of the domain**; the B-PINN cannot produce such violations

---

## Experimental Analysis

<div style="margin-bottom: 30px;">
<h3>Parameter-Space Coverage</h3>
<p>Distribution comparison between the FEM-generated synthetic dataset (2,000 simulations) and the 275 field case histories across six input parameters: height, slope angle, unit weight, cohesion, friction angle, and pore-pressure ratio. The synthetic data provides broader coverage to support pre-training, while the field cases concentrate on ranges commonly encountered in practice.</p>
<img src="/images/research-projects/807bb3c5-1cfd-4035-b9e2-39cffd2374b9-1785841422037_image.png" alt="Parameter-space coverage: synthetic vs reference cases" style="max-width: 100%; border: 1px solid #ddd; border-radius: 4px; padding: 4px;">
<p style="text-align: center; font-style: italic; color: #666; font-size: 0.9em;">Figure: Parameter-space coverage — synthetic (FEM-generated) vs. reference field cases</p>
</div>

<div style="margin-bottom: 30px;">
<h3>Physical Consistency of Candidate Models</h3>
<p>(a) Heatmap of monotonicity violations broken down by input parameter and model — darker shading indicates more frequent violations. The B-PINN columns show dashes (no violations possible by construction). (b) Overall monotonicity violation measure on a relative scale, confirming that the B-PINN (both base and pre-trained variants) records zero violations while all conventional baselines exhibit worst-case violations.</p>
<img src="/images/research-projects/ce399e3d-f2cd-4734-ad62-57430691d518-1785841430261_image.png" alt="Physical consistency of candidate models" style="max-width: 100%; border: 1px solid #ddd; border-radius: 4px; padding: 4px;">
<p style="text-align: center; font-style: italic; color: #666; font-size: 0.9em;">Figure: Physical consistency — (a) violations by input, (b) overall monotonicity measure</p>
</div>

<div style="margin-bottom: 30px;">
<h3>Predictive Performance Across Evaluation Metrics</h3>
<p>Five-fold cross-validation results comparing all six models across accuracy, precision, recall, F1-score, and AUC. Bars show fold means; whiskers show spread. Purple denotes conventional baselines; green denotes the proposed physics-informed models. Despite slightly lower point estimates, the B-PINN's performance is statistically indistinguishable from the baselines.</p>
<img src="/images/research-projects/e998d733-3eb6-4256-a0ea-2f4d0458f848-1785841437476_image.png" alt="Predictive performance across evaluation metrics" style="max-width: 100%; border: 1px solid #ddd; border-radius: 4px; padding: 4px;">
<p style="text-align: center; font-style: italic; color: #666; font-size: 0.9em;">Figure: Predictive performance — five-fold cross-validation across evaluation metrics</p>
</div>

---

## My Contributions

- Developed the complete modeling pipeline: data curation (275 field cases + 2,000 FEM simulations), architecture design, training, and evaluation
- Designed and implemented the hard-monotone Bayesian neural network architecture with architectural monotonicity enforcement
- Conducted the full comparative analysis including SHAP-based interpretability, McNemar's testing, and design-chart generation

---

## Publications

1. **Hasnat, N.** (2026). "Physically Admissible Slope-Stability Prediction Using a Hard-Monotone Bayesian Physics-Informed Neural Network." *(Manuscript in Preparation)*
