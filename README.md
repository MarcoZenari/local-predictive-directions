# Local Predictive Directions (LPD)

Code for the paper

> **Self-Supervised Learning of Local Predictive Directions as a Neural Computation**
> Marco Zenari, Xuehao Ding, Daniel Burnham, Austin R. Ellis-Mohr, Anirvan M. Sengupta, Dmitri Chklovskii
> *NeurReps Workshop 2026, Proceedings of Machine Learning Research (PMLR)*

LPD learns local directions in state space whose projections best predict near-future
trajectory evolution. It applies past–future CCA to temporal differences, which makes it
invariant to translations of the state. A non-negative similarity-matching objective
partitions trajectories into predictive domains. The objective has offline and online
algorithms; the online one maps onto a network with feedforward weights, lateral
competition and rectified activity.

## Repository structure

```
notebooks/
  dynamical_systems.ipynb   # Fig. 2, Fig. 4, Fig. 6, Fig. 9
  robustness_glv.ipynb      # Fig. 5, Fig. 8
  lpd_vs_gmm_sphere.ipynb   # Fig. 10, Fig. 11
  spatial_filters.ipynb     # Fig. 3b (left)
  temporal_filters.ipynb    # Fig. 3b (right)
```

| Notebook | Content | Paper |
|---|---|---|
| `dynamical_systems.ipynb` | Offline/online LPD; affine saddle, gLV heteroclinic channel, two-saddle sphere | Sec. 3, Fig. 2 |
| | CCA benchmark with a Gaussian latent variable | App. F, Fig. 4 |
| | Model selection (objective, precision, recall vs. *k*) | App. J, Fig. 6 |
| | Ablation of finite differences and non-negativity | App. L, Fig. 9 |
| `robustness_glv.ipynb` | Scaling with the number of species *N*; finite-difference lag τ | App. I.3, Fig. 5; App. K, Fig. 8 |
| `lpd_vs_gmm_sphere.ipynb` | LPD vs. Gaussian mixture model in tangent space; time-lagged mutual information | App. M, Figs. 10–11 |
| `spatial_filters.ipynb` | Center–surround ON/OFF spatial filters from 1D dead-leaves stimuli | Sec. 4, Fig. 3b |
| `temporal_filters.ipynb` | Sustained/transient ON/OFF temporal filters | Sec. 4, Fig. 3b |

## Installation

```bash
git clone https://github.com/<user>/local-predictive-directions.git
cd local-predictive-directions
pip install -r requirements.txt
```

Tested with Python 3.10+. A CUDA GPU is used automatically when available; all notebooks also
run on CPU, but the larger sweeps (`robustness_glv.ipynb`, the ablation in
`dynamical_systems.ipynb`) are slow.

## Usage

```bash
cd notebooks
jupyter lab
```

Each notebook writes figures to `results/` and intermediate results (`.npz`, `.csv`, `.pkl`)
to `data/`, relative to the working directory. Change `RESULTS_DIR` and `DATA_DIR` in the first
cell to use other locations.

## Citation

```bibtex
@InProceedings{zenari26,
  title     = {Self-Supervised Learning of Local Predictive Directions as a Neural Computation},
  author    = {Zenari, Marco and Ding, Xuehao and Burnham, Daniel and Ellis-Mohr, Austin R. and Sengupta, Anirvan M. and Chklovskii, Dmitri},
  booktitle = {Proceedings of the NeurReps Workshop 2026},
  series    = {Proceedings of Machine Learning Research},
  publisher = {PMLR},
  year      = {2026}
}
```

## License

<!-- TODO: choose a license (e.g. MIT) and add a LICENSE file -->
