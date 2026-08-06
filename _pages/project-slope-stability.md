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

The network is pre-trained on 2,000 finite-element simulations sampled from a 2,707-case pool generated in PLAXIS 2D and fine-tuned on 275 audited field case histories. Tuned classical baselines (Random Forest, SVM, ANN, BNN) achieve higher cross-validation accuracy than the B-PINN, but  every baseline violates monotonicity, while the B-PINN records zero violations, including outside its training range. Pretraining the model assists in counterbalancing the the lack of data somewhat through improved performance metrices.

**Research Period:** 2025 – Present &nbsp;|&nbsp; **Status:** Manuscript in Preparation

---

## Key Findings
-Deterministic models such as RF, SVM, and ANN give better results compared to probabilistic models, although they exhibit monotonicity violations.
- The B-PINN achieves **zero monotonicity violations** across all parameter responses, while conventional baselines violate monotonicity in **19–31%** of out-of-range parameter sweeps
- SHAP analysis of the unconstrained BNN shows it assigns **lower failure probability to higher pore pressure** (Spearman ρ = −0.90), a physically inadmissible pattern
- In an 88,200-point design chart, the unconstrained network predicts decreasing failure probability with increasing slope height across **46% of the domain**; the B-PINN cannot produce such violations

---

## Analysis

<div style="margin-bottom: 30px;">
<h3>Parameter-Space Coverage</h3>
<p>Distribution comparison between the FEM-generated synthetic dataset (2,000 simulations) and the 275 field case histories across six input parameters: height, slope angle, unit weight, cohesion, friction angle, and pore-pressure ratio. The synthetic data provides broader coverage to support pre-training, while the field cases concentrate on ranges commonly encountered in practice.</p>
<img src="/images/research-projects/Slope Stability_FEM Data.png" alt="Parameter-space coverage: synthetic vs reference cases" style="max-width: 100%; border: 1px solid #ddd; border-radius: 4px; padding: 4px;">
<p style="text-align: center; font-style: italic; color: #666; font-size: 0.9em;">Figure: Parameter-space coverage — synthetic (FEM-generated) vs. reference field cases</p>
</div>

<div style="margin-bottom: 30px;">
<h3>Predictive Performance Across Evaluation Metrics</h3>
<p>Five-fold cross-validation results comparing all six models across accuracy, precision, recall, F1-score, and AUC. Bars show fold means; whiskers show spread. Purple denotes conventional baselines; green denotes the proposed physics-informed models. Despite slightly lower point estimates, the B-PINN's performance is statistically indistinguishable from the baselines.</p>
<img src="/images/research-projects/Slope Stability_Five fold.png" alt="Predictive performance across evaluation metrics" style="max-width: 100%; border: 1px solid #ddd; border-radius: 4px; padding: 4px;">
<p style="text-align: center; font-style: italic; color: #666; font-size: 0.9em;">Figure: Predictive performance — five-fold cross-validation across evaluation metrics</p>
</div>


<div style="margin-bottom: 30px;">
<h3>Physical Consistency of Candidate Models</h3>
<p>(a) Heatmap of monotonicity violations broken down by input parameter and model — darker shading indicates more frequent violations. The B-PINN columns show dashes (no violations possible by construction). (b) Overall monotonicity violation measure on a relative scale, confirming that the B-PINN (both base and pre-trained variants) records zero violations while all conventional baselines exhibit worst-case violations.</p>
<img src="/images/research-projects/Slope Stability_Physical Consistancy.png" alt="Physical consistency of candidate models" style="max-width: 100%; border: 1px solid #ddd; border-radius: 4px; padding: 4px;">
<p style="text-align: center; font-style: italic; color: #666; font-size: 0.9em;">Figure: Physical consistency — (a) violations by input, (b) overall monotonicity measure</p>
</div>

---

## My Contributions

- Developed the complete modeling pipeline: data curation (275 field cases + 2,000 FEM simulations), architecture design, training, and evaluation
- Designed and implemented the hard-monotone Bayesian neural network architecture with architectural monotonicity enforcement
- Conducted the full comparative analysis including SHAP-based interpretability, McNemar's testing, and design-chart generation

---

## Publications (Yet to be submitted) 

1. "Physically Admissible Slope-Stability Prediction Using a Hard-Monotone Bayesian Physics-Informed Neural Network." *(Manuscript in Preparation)*
