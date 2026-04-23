# ExoNet: Calibrated Multimodal Deep Learning for TESS Exoplanet Candidate Vetting

[![arXiv](https://img.shields.io/badge/arXiv-2604.15560-b31b1b.svg)](https://arxiv.org/abs/2604.15560)
[![Zenodo](https://zenodo.org/badge/DOI/10.5281/zenodo.19708949.svg)](https://doi.org/10.5281/zenodo.19708949)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Author:** Md. Rashadul Islam  
**Institution:** Daffodil International University, Dhaka, Bangladesh  
**Contact:** islam15-6062@s.diu.edu.bd

---

## Overview

ExoNet is a calibrated multimodal deep learning framework for automated vetting of TESS exoplanet candidates. It jointly encodes:

- **Global view** — phase-folded light curve (1 × 1001 bins)
- **Local view** — transit-centred light curve (1 × 1001 bins)
- **Stellar parameters** — 8 scalar features (period, depth, radius, Teq, Teff, log g, [Fe/H])

through a trimodal **1D CNN + 8-head Multi-Head Attention + Residual Late Fusion** architecture, with post-hoc **Temperature Scaling** (T* = 1.573) for calibrated probability output.

---

## Key Results

| Metric | Value |
|--------|-------|
| Test AUC (Kepler) | **0.9549** |
| Validation AUC | 0.9487 |
| Accuracy | 86.3% |
| TESS candidates analysed | 4,720 |
| High-confidence (≥70%) | **1,754** |
| Habitable-zone candidates | **52** |
| Rocky HZ candidates (Rp < 1.6 R⊕) | **6** |
| Post-hoc confirmed planets (2026) | **3** (TOI-6716, TOI-7384, TOI-2094) |

**TOI-6716.01** — ranked at 92.2% confidence by ExoNet — was independently confirmed as a terrestrial planet (Rb = 0.98 ± 0.07 R⊕, M4 host star) in 2026, providing prospective validation of the calibrated rankings.

---

## Repository Structure

```
ExoNet_TESS_Candidates/
├── exonet_v6.ipynb          # Main training + inference notebook
├── requirements.txt         # Python dependencies
├── models/
│   └── temperature.json     # Calibration parameter (T* = 1.573)
├── figures/
│   ├── evaluation_results.png
│   ├── training_curves.png
│   ├── calibration_plot.png
│   └── tess_analysis.png
└── README.md
```

> **Note:** Model weights (`best_model.pth`) and candidate catalogues are archived on Zenodo.  
> Full data: [https://doi.org/10.5281/zenodo.19708949](https://doi.org/10.5281/zenodo.19708949)

---

## Installation

```bash
git clone https://github.com/Rashadul22/ExoNet_TESS_Candidates.git
cd ExoNet_TESS_Candidates
pip install -r requirements.txt
```

---

## Data

All training and inference data are publicly available:

| Source | URL |
|--------|-----|
| Kepler KOI catalogue | [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu) |
| TESS TOI catalogue | [NASA Exoplanet Archive](https://exoplanetarchive.ipac.caltech.edu) |
| Light curves | [MAST Archive](https://mast.stsci.edu) |
| ExoNet candidate catalogue | [Zenodo DOI: 10.5281/zenodo.19708949](https://doi.org/10.5281/zenodo.19708949) |

---

## Citation

If you use ExoNet in your research, please cite:

```bibtex
@article{Islam2026ExoNet,
  author  = {Islam, Md. Rashadul},
  title   = {ExoNet: A Calibrated Multimodal Deep Learning Framework
             for TESS Exoplanet Candidate Vetting with Phase-Folded
             Light Curves, Stellar Parameters, and Multi-Head Attention},
  journal = {arXiv e-prints},
  year    = {2026},
  note    = {arXiv:2604.15560; submitted to MNRAS}
}
```

---

## Architecture

```
Global View (1×1001) ──► 1D CNN + 8-head MHA ──► h_g ∈ R^256 ─┐
Local View  (1×1001) ──► 1D CNN + 8-head MHA ──► h_l ∈ R^256 ─┼──► Concat (640-d)
Stellar Params  (8,) ──► MLP (64→128)         ──► h_s ∈ R^128 ─┘
                                                        │
                                              Residual Fusion MLP
                                              (512 → 256, dropout 0.4)
                                                        │
                                              Classifier (256→64→2)
                                                        │
                                              Temperature Scaling T*=1.573
                                                        │
                                              P(planet) ∈ [0, 1]
```

---

## License

This project is licensed under the MIT License.  
Candidate catalogue data is released under CC BY 4.0 via Zenodo.
