# Quantum-Dot–Microcavity Dynamics

Numerical reproduction of Perea, Porras & Tejedor (2004): quantum-dot–microcavity dynamics, photon statistics, and emission spectra.

The notebook integrates the density-matrix equations for a quantum dot coupled to a cavity with incoherent pumping and dissipation. It calculates populations, coherences, the mean photon number, second-order photon correlations, and emission spectra for the cavity and exciton channels.

## Reference

J. I. Perea, D. Porras, and C. Tejedor, *Dynamics of the excitations of a quantum dot in a microcavity*, Physical Review B **70**, 115304 (2004).

DOI: [10.1103/PhysRevB.70.115304](https://doi.org/10.1103/PhysRevB.70.115304).

## Notebook contents

| Cells | Calculation |
| --- | --- |
| 1–5 | Population dynamics: `resolver_y_graficar` |
| 6–8 | Density-matrix elements: `graficar_elemento_matriz` |
| 9–11 | Mean photon number maps: `mapa_Nph` |
| 12–14 | Second-order correlation maps: `mapa_g2` |
| 15–18 | Time-dependent correlations: `resolver_correlacion_QRT` |
| 19–23 | Stationary emission spectra: `graficar_espectro_emision` |

Cell numbers start at 1. Energies and input rates are expressed in meV, and times in ps. The notebook uses `HBAR = 0.6582119569` meV·ps.

The spectrum function computes its own stationary state, evolves the correlation functions with BDF, and performs the spectral transformation using Simpson weights and ZoomFFT.

## Run locally

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
jupyter lab
```

On Windows PowerShell, activate the environment with `.venv\Scripts\Activate.ps1`.

Open `notebooks/reproduccion_tejedor.ipynb` in Jupyter. Alternatively, upload that notebook to Google Colab.

Run each function-definition cell before its examples. Cell 16 creates `datos_rho` for cells 17 and 18. The spectral calculations can be run separately by executing cell 19 followed by one of cells 20–23.

The original parameter scans and spectral examples may take substantial time. The spectrum function defaults to `tau_final=5000` ps and checks the decay of the correlations. Smaller grids and photon cutoffs can be used for exploratory runs; convergence must be checked before interpreting physical results.

## Repository structure

| Path | Purpose |
| --- | --- |
| `notebooks/reproduccion_tejedor.ipynb` | Original calculation code, with saved outputs cleared |
| `requirements.txt` | NumPy, SciPy, Matplotlib, and JupyterLab |
| `.gitignore` | Local environments, Python caches, and notebook checkpoints |

## Reproduction status

This is a reproduction in progress. All 23 code cells passed syntax checks during repository preparation. The complete simulations and agreement with the paper's figures have not been independently validated in this preparation step.

Before comparing spectra with the article, check photon-space truncation, the correlation tail, energy resolution, and normalization. Dependency versions are not pinned because the source notebook does not provide a frozen original environment.

## Code preservation

The notebook's 23 code cells are preserved without changes to equations or parameters. Saved outputs, execution counts, and session metadata were removed for version control.
