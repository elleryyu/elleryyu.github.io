---
title: 'Understanding fMRI: A Foundation Guide for Computational Researchers'
date: 2026-03-01
permalink: /posts/2026/03/fmri-foundations/
tags:
  - neuroimaging
  - fMRI
  - neuroscience
  - methods
---

Functional MRI (fMRI) is one of the most widely used tools in human neuroscience. For computational researchers entering the field, understanding what fMRI actually measures — and what it doesn't — is essential before any modeling begins.

---

## What fMRI Measures: The BOLD Signal

fMRI does not directly measure neural activity. It measures the **Blood-Oxygen-Level-Dependent (BOLD)** signal — a proxy for neural activity based on local changes in blood oxygenation.

When neurons fire, they consume oxygen. The brain compensates with a localized increase in blood flow (neurovascular coupling), delivering more oxygenated hemoglobin than is actually consumed. Because oxygenated and deoxygenated hemoglobin have different magnetic properties, this change is detectable in MRI.

The BOLD signal is:
- **Indirect** — it reflects hemodynamic response, not electrical activity
- **Slow** — the hemodynamic response peaks ~5–6 seconds after a neural event
- **Noisy** — corrupted by motion, cardiac pulsation, respiration, and scanner drift

---

## Task fMRI vs. Resting-State fMRI

**Task fMRI (tfMRI)** presents stimuli or instructions and contrasts activation patterns between conditions (e.g., viewing faces vs. objects). It reveals which regions are *engaged by* specific cognitive demands.

**Resting-state fMRI (rs-fMRI)** acquires data while subjects lie still with no explicit task. Even at rest, the brain exhibits structured, spontaneous fluctuations that reflect its intrinsic organization. These correlations between regions define **functional connectivity (FC)** — the backbone of large-scale brain network research.

Resting-state is particularly valuable for clinical populations (pediatric, psychiatric) where compliance with task paradigms is difficult.

---

## Functional Connectivity

The most common rs-fMRI analysis computes the **Pearson correlation** between BOLD time series of pairs of brain regions (defined by a parcellation atlas). This yields a connectivity matrix that encodes how synchronized two regions are over the scan.

Common approaches:
- **Seed-based correlation** — pick one region, correlate with all others
- **Independent Component Analysis (ICA)** — data-driven decomposition into spatiotemporal components
- **Parcellation-based FC matrix** — parcellate the brain into N regions, compute N×N correlation matrix

The result is typically used as input to downstream analyses: group comparison, machine learning, or graph-theoretic measures.

---

## Key Preprocessing Steps

Raw fMRI data requires extensive preprocessing before analysis:

1. **Slice timing correction** — MRI slices are acquired sequentially, not simultaneously
2. **Motion correction** — realign volumes to a reference; regress out motion parameters
3. **Distortion correction** — correct EPI geometric distortions using fieldmaps
4. **Registration** — align functional to structural MRI, then to standard space (MNI152)
5. **Smoothing** — spatial Gaussian smoothing improves SNR but reduces spatial resolution
6. **Nuisance regression** — remove signal from white matter, CSF, global signal, motion

Common pipelines: **fMRIPrep**, **HCP Pipelines**, **AFNI**, **FSL FEAT**.

---

## Parcellation Atlases

To reduce dimensionality, the brain is divided into regions of interest (ROIs) using a parcellation atlas. Common choices:

| Atlas | Parcels | Notes |
|-------|---------|-------|
| AAL | 116 | Anatomical, widely used |
| Schaefer | 100–400 | Functional, cortex only |
| Glasser HCP | 360 | Multi-modal, high resolution |
| Power264 | 264 | Sphere ROIs, functional |

The choice of atlas affects downstream results and comparisons. Consistency within a study is critical.

---

## Temporal Dynamics Beyond Static FC

Static FC (time-averaged correlation) discards temporal information. Recent work has moved toward:

- **Dynamic FC** — windowed correlations or HMM-based state decomposition
- **Intrinsic Neural Timescales (INT)** — the autocorrelation decay constant of regional BOLD, reflecting how long a region integrates information over time
- **Temporal hierarchy** — the gradient of timescales across cortex, from early sensory (fast) to association areas (slow)

These temporal features capture aspects of brain organization invisible to static connectivity analyses.

---

## Common Pitfalls

- **Motion artifact** is the single largest confound in fMRI. Subjects who move more tend to show spuriously higher short-range connectivity. Careful scrubbing (removing high-motion volumes) is essential.
- **Global signal regression (GSR)** is controversial — it removes a shared component that may be neurally meaningful or artifactual.
- **Multiple comparisons** — brain-wide analyses involve thousands of tests; FDR or permutation-based correction is required.

---

## Further Reading

- Logothetis, N. K. (2008). What we can do and what we cannot do with fMRI. *Nature*, 453, 869–878.
- Power, J. D. et al. (2012). Spurious but systematic correlations in functional connectivity MRI networks arise from subject motion. *NeuroImage*, 59, 2142–2154.
- Huntenburg, J. M. et al. (2018). Large-scale gradients in human cortical organization. *Trends in Cognitive Sciences*, 22, 21–31.

---

*This post is part of a series on neuroimaging foundations for computational researchers.*
