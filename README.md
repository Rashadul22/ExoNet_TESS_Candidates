# ExoNet: Calibrated Multimodal Deep Learning for TESS Exoplanet Vetting

[![arXiv](https://img.shields.io/badge/arXiv-2604.15560-b31b1b.svg)](https://arxiv.org/abs/2604.15560)
[![Zenodo](https://zenodo.org/badge/DOI/10.5281/zenodo.19708949.svg)](https://doi.org/10.5281/zenodo.19708949)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Author:** Md. Rashadul Islam — Daffodil International University, Dhaka, Bangladesh  
**Paper:** [arXiv:2604.15560](https://arxiv.org/abs/2604.15560) | Submitted to MNRAS  
**Catalogue:** [Zenodo DOI: 10.5281/zenodo.19708949](https://doi.org/10.5281/zenodo.19708949)

---

## What is ExoNet?

ExoNet is a calibrated multimodal deep learning pipeline for automated vetting of TESS exoplanet candidates. NASA's TESS had over 7,800 planet candidates by early 2026, yet fewer than 720 were confirmed — ExoNet helps close this gap by ranking all 4,720 unconfirmed Planet Candidates with calibrated confidence scores.

---

## Key Results

| Metric | Value |
|--------|-------|
| Test AUC (Kepler held-out) | **0.9549** |
| Classification accuracy | **86.3%** |
| TESS candidates analysed | 4,720 |
| High-confidence ≥70% | **1,754** |
| Habitable-zone candidates | **52** |
| Rocky HZ candidates (Rp < 1.6 R⊕) | **6** |
| Post-hoc confirmed planets (2026) | **3** |

> **TOI-6716.01** — ranked at 92.2% confidence by ExoNet — was independently confirmed as a terrestrial planet (Rb = 0.98 R⊕, M4 dwarf host) in 2026, providing prospective validation of the calibrated rankings.

---

## Model Architecture
