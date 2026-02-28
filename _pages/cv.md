---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

{% include base_path %}

Education
======
* **Master in Computer Science**, University of Virginia, Charlottesville, VA (GPA: 3.77/4.00) — 2023–2025
* **B.S. in Computer Science** (Cum Laude), Kean University, Wenzhou, China | Union, NJ (GPA: 3.55/4.00) — 2019–2023

Research interests
======
* **Computational neuroimaging:** brain network analysis, multimodal MRI and behavioral data integration, brain–behavior modeling, and biomarker identification.
* **Deep learning for brain science:** graph neural networks (GNNs), self-supervised and foundation models, multimodal fusion, representation learning, and interpretable machine learning.

Research experience
======
* **Research Assistant**, Neurobioinformatics Lab, University of Virginia, Charlottesville, VA (Apr 2024 – Present) — *Mentored by Prof. Aiying Zhang*
  * Developed and evaluated a GNN-based framework integrating fMRI neuroimaging with behavioral measures under supervised and unsupervised paradigms; preliminary findings accepted at MIDL 2025.
  * Built an intrinsic neural timescale (INT)–based analysis pipeline on ACE and ABIDE; preliminary results accepted at SPIE Medical Imaging 2025.
  * Implemented trial-wise beta estimation workflows (LSS/LSA) and beta-series correlation (BSC) pipelines for task fMRI (SST, MID), enabling robust analyses of task-evoked functional connectivity.
  * Managed datasets containing Controlled Unclassified Information (CUI), ensuring rigorous curation, role-based access control, and NIST SP 800-171–aligned handling in coordination with UVA Research Computing.
  * Designed, built, and maintain the lab website; organize and host the lab’s biweekly journal club.

* **Research Volunteer**, Song Lab, University of Florida, Remote (Jan 2024 – May 2024) — *Mentored by Prof. Qianqian Song*
  * Contributed to a genome-wide association study meta-analysis on immune-related adverse events (irAEs).
  * Curated and organized drug treatment datasets across multiple cancer types for downstream analyses.
  * Collaborated with lab members on preliminary analysis and interpretation of genetic data.

* **Research Assistant**, Institute of Societal Contemporary Computing, Wenzhou-Kean University, Wenzhou, China (Sep 2021 – Jun 2023) — *Mentored by Prof. Sujatha Krishnamoorthy*
  * Led a student team in developing AI/ML-driven methods for assessing Parkinson’s disease based on written tasks, voice patterns, and gait analysis.
  * Compiled a survey on state-of-the-art methods for Parkinson’s disease diagnostics across behavioral perspectives.
  * Organized and optimized code provided by collaborators for a diabetic retinopathy detection project, submitting detailed reports to the advisor.

Internship experience
======
* **Software Development Engineer**, Zhuanzhuan Spirit Tech Co. Ltd., Beijing, China (Dec 2021 – Feb 2022) — *Supervised by Mr. Yuan Wang*
  * Developed an information management system using Spring Framework, improving data processing efficiency and scalability.
  * Contributed to the development and troubleshooting of the Phone Detection “One Line” system, enhancing its accuracy.
  * Prepared and delivered weekly reports during team meetings; managed communication with the product manager to align technical development with product goals.

Teaching experience
======
  <ul>{% for post in site.teaching reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

Research grant support
======
* **UVA Brain Institute 2024 Transformative Neuroscience Pilot Grants** (PI: Dr. Sequeira and Zhang) — *Investigating anxiety-related variability in brain structure–function coupling during adolescence.* Role: Data Management Technician.
* **R01AG082228** (MPIs: Dr. Gibson, Flowers and Zhang) — *Mechanistic links between the benefits of pharmacologically high thiamine (vitamin B1) in Alzheimer’s disease to Advanced Glycation Endproducts (AGE).* Role: Statistical Analyst.

Mentoring experience
======
* Aroosha Solomon, B.A. Biology, Distinguished Majors Program (DMP), University of Virginia (Jun 2024 – Present)
* Amy Chang, B.A. Human Biology (DMP), University of Virginia (Oct 2024 – May 2025)
* Junkai Zhang, PhD Student, University of Illinois at Chicago (Sep 2024 – May 2025)
* Mackenzie Bullock, Undergraduate Student, University of Virginia (Nov 2024 – May 2025)
* Chloe Wang, Undergraduate Student, University of Virginia (Feb 2025 – May 2025)

Publications
======
  <ul>{% for post in site.publications reversed %}
    {% include archive-single-cv.html %}
  {% endfor %}</ul>

Presentations
======
  <ul>{% for post in site.talks reversed %}
    {% include archive-single-talk-cv.html %}
  {% endfor %}</ul>

Skills
======
* **Languages:** Python, Java, HTML5, LaTeX, R, SQL
* **Tools:** PyTorch, DGL, Docker, FSL, fMRIprep, Nilearn, FreeSurfer, Connectome Workbench, METAL
