---
title: "Understanding dMRI: Mapping the Brain's White Matter Highways"
date: 2026-03-04
permalink: /posts/2026/03/dmri-foundations/
tags:
  - neuroimaging
  - dMRI
  - diffusion MRI
  - tractography
  - neuroscience
  - methods
---

While fMRI probes functional activity, **diffusion MRI (dMRI)** maps the *structural* wiring of the brain — the white matter pathways that physically connect regions across the cortex. Together, they form the two pillars of human connectomics.

---

## The Physics: Diffusion of Water

dMRI exploits the fact that water molecules in biological tissue don't diffuse freely — their movement is constrained by cellular structure. In white matter, axon bundles act as tubes: water diffuses preferentially *along* fibers, not across them.

By applying magnetic field gradients in multiple directions and measuring how signal attenuates, MRI can infer the **local diffusion profile** at each voxel — and from that, infer fiber orientation.

---

## Key Diffusion Models

### Diffusion Tensor Imaging (DTI)

The most widely used model. Fits a 3D ellipsoid (tensor) to the diffusion profile at each voxel.

From the tensor, we extract:
- **Fractional Anisotropy (FA)** — how directional the diffusion is (0 = isotropic, 1 = perfectly anisotropic). Higher FA ≈ more intact/coherent white matter.
- **Mean Diffusivity (MD)** — average diffusion magnitude; increases in edema, neurodegeneration
- **Axial Diffusivity (AD)** — diffusion along the principal axis (along fibers)
- **Radial Diffusivity (RD)** — diffusion perpendicular to fibers; sensitive to myelin integrity

**Limitation**: DTI assumes one fiber population per voxel. In regions of crossing fibers (~90% of white matter), it fails.

### HARDI and CSD

**High Angular Resolution Diffusion Imaging (HARDI)** samples many more gradient directions, enabling models that capture multiple fiber orientations per voxel.

**Constrained Spherical Deconvolution (CSD)** estimates the fiber orientation distribution (FOD) — a continuous function describing the probability of fiber orientations. This is the basis for modern tractography.

### Diffusion Kurtosis Imaging (DKI)

Extends DTI by modeling non-Gaussian diffusion behavior. Provides additional metrics (mean kurtosis) sensitive to tissue complexity beyond DTI.

---

## Tractography: Reconstructing White Matter Pathways

Tractography traces streamlines through the diffusion field, connecting voxels along their estimated fiber orientations. It is the primary tool for studying **structural connectivity**.

### Deterministic Tractography
Follows the principal diffusion direction at each step. Fast, intuitive, but sensitive to noise and fails at fiber crossings.

### Probabilistic Tractography
Samples from the FOD uncertainty distribution at each step. Produces connectivity probability maps rather than discrete streamlines. More robust, but computationally expensive and prone to false positives at long range.

### Structural Connectome
By combining tractography with a brain parcellation, we can build a **structural connectivity matrix** analogous to fMRI's functional connectivity matrix — where each entry reflects the number or density of streamlines connecting two regions.

Popular tools: **MRtrix3**, **FSL FDT**, **DSI Studio**, **Dipy**.

---

## dMRI Preprocessing

1. **Denoising** — MP-PCA or patch2self to remove thermal noise
2. **Gibbs ringing correction** — artifact from k-space truncation
3. **Motion & eddy current correction** — especially important for high b-value data
4. **Susceptibility distortion correction** — using reverse phase-encode B0 pairs
5. **Bias field correction**
6. **Registration** to T1w and standard space

The **dMRIPrep** and **QSIPrep** pipelines provide standardized, reproducible preprocessing.

---

## Structural vs. Functional Connectivity

A central question in connectomics: how does structural connectivity (SC) constrain functional connectivity (FC)?

The SC–FC relationship is positive but moderate (r ~ 0.3–0.6 in most studies). Regions with strong white matter connections tend to have correlated BOLD signals, but FC also emerges between regions without direct structural links — mediated through polysynaptic paths or shared inputs.

Multimodal integration of SC and FC is an active research area, with graph neural networks emerging as a natural framework for joint modeling.

---

## Clinical Applications

dMRI has revealed white matter abnormalities in:
- **Autism Spectrum Disorder** — altered long-range connectivity, atypical myelination
- **Schizophrenia** — widespread FA reductions, especially in frontal-temporal tracts
- **Traumatic Brain Injury** — diffuse axonal injury invisible on conventional MRI
- **Multiple Sclerosis** — lesion detection and tract-specific damage quantification
- **Normal aging** — progressive white matter degradation from mid-adulthood onward

---

## Limitations and Open Challenges

- Tractography **cannot resolve fiber crossings** reliably at standard resolution
- Streamline counts are **not quantitative** measures of connectivity strength
- **False positive streamlines** are prevalent, especially for long-range connections
- dMRI is **indirect** — it infers microstructure from bulk water diffusion
- Reproducibility across sites and scanners remains a challenge despite harmonization efforts

---

## Further Reading

- Basser, P. J. et al. (1994). MR diffusion tensor spectroscopy and imaging. *Biophysical Journal*, 66, 259–267.
- Tournier, J. D. et al. (2019). MRtrix3: A fast, flexible and open software framework for medical image processing and visualisation. *NeuroImage*, 202, 116137.
- Jeurissen, B. et al. (2019). Diffusion MRI fiber tractography of the brain. *NMR in Biomedicine*, 32, e3785.
- Sotiropoulos, S. N. & Zalesky, A. (2019). Building connectomes using diffusion MRI: why, how and but. *NMR in Biomedicine*, 32, e3752.

---

*This post is part of a series on neuroimaging foundations for computational researchers.*
