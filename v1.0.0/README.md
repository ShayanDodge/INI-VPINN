# INI-VPINN v1.0.0

Homogeneous T-shaped domain benchmark for **INI-VPINN**.

This release provides a complete notebook workflow for training, operator-guided test-function selection, FEM validation, and convergence/error visualization.

## Main notebook

`INI_VPINN_v1.0.0_Homogeneous.ipynb`

The notebook includes:

- Gauss-Lobatto-Jacobi quadrature
- Jacobi and trigonometric test functions
- element-wise test-function configuration
- pre-training operator visualization
- INI-VPINN training
- FEM comparison and error metrics
- error history versus wall-clock time and iterations

## Operator settings

Main parameters:

```python
N_el_x = 4
N_el_y = 4
N_quad = 7

N_test_x = N_el_x * [5]
N_test_y = N_el_y * [5]

Net_layer = [2] + [18] * 8 + [1]
N_TRAIN_ITER = 80000 + 1
```

Test functions are selected by element:

```python
default_type = "jacobi"

element_types_x = {
    1: "trig1to0",
    5: "trig1to0",
    2: "trig0to1",
    6: "trig0to1",
}

element_types_y = {
    8: "trig1to0",
    11: "trig1to0",
    12: "trig0to1",
    13: "trig0to1",
    14: "trig0to1",
    15: "trig0to1",
}
```

Useful rule:

```text
x: LEFT -> trig1to0, RIGHT -> trig0to1
y: BOTTOM -> trig1to0, TOP -> trig0to1
otherwise -> jacobi
```

For setup and verification:

```python
SHOW_SUBDOMAIN_NUMBERS = True
SHOW_TEST_CONFIG = True
SHOW_TEST_FAMILIES = True
```

## Included files

```text
INI_VPINN_v1.0.0_Homogeneous.ipynb
V_T_200.txt
INIVPINN_TD.txt
INI_ERROR_VS_WALLTIME.npz
Tshape_FEM_INI_Homogeneous.png
Tshape_FEM_INI_Homogeneous.pdf
ERROR_VS_WALLTIME_AND_EPOCHS_INI.png
```

## Benchmark result

For the supplied homogeneous T-shaped case:

- MAE: `1.57e-03`
- RMSE: `1.85e-03`
- MAPE: `0.31%`

## Run

Open the notebook and execute the cells in order.

For a quick smoke test:

```python
N_TRAIN_ITER = 100
```

Then restore the full training value for the final run.

## Citation

If you use this code or results, please cite the INI-VPINN paper:

> Shayan Dodge et al., **“INI-VPINN: A Variational Physics-Informed Neural Network with Implicit Neumann and Interface Handling for Multi-Material Domains with Geometric Singularities,”** Journal of Computational Physics, 2026.

**Authors:** Shayan Dodge, Alessandro Formisano, Sami Barmada  
**Journal:** *Journal of Computational Physics (JCP)*  
**DOI:** `10.1016/j.jcp.2026.115328`    
**Links:**  [ScienceDirect](https://doi.org/10.1016/j.jcp.2026.115328) ·[arXiv](https://arxiv.org/abs/2606.18032) ·[ResearchGate](https://www.researchgate.net/publication/413656372_INI-VPINN_A_Variational_Physics-Informed_Neural_Network_with_Implicit_Neumann_and_Interface_Handling_for_Multi-Material_Domains_with_Geometric_Singularities)

BibTeX:

```bibtex
@article{dodge2026inivpinn,
title = {INI-VPINN: A variational physics-informed neural network with implicit neumann and interface handling for multi-material domains with geometric singularities},
journal = {Journal of Computational Physics},
volume = {565},
pages = {115328},
year = {2026},
issn = {0021-9991},
doi = {https://doi.org/10.1016/j.jcp.2026.115328},
url = {https://www.sciencedirect.com/science/article/pii/S0021999126006777},
author = {Shayan Dodge and Alessandro Formisano and Sami Barmada},
keywords = {Physics-informed neural networks (PINNs), Variational PINN (VPINN), Petrov-Galerkin method, Weak-form learning, Neumann and interface conditions, Multi-material domains, Geometric singularities},
abstract = {We propose a new weak-form Physics-Informed Neural Network approach (named INI-VPINN). INI-VPINN naturally incorporates Neumann boundary and interface conditions into the variational formulation. It removes the need for additional loss terms or multiple subdomain networks. This framework employs compact support weighting functions and integration by parts to implicitly impose flux and continuity constraints. In this way, it implicitly ensures physical consistency across material boundaries. The proposed method is tested on Poisson and Laplace problems with sharp interfaces and complex geometries. Results show that, compared with several other Physics Informed Neural Networks-based formulations, the INI-VPINN consistently achieves higher accuracy, smoother and faster convergence. The proposed framework provides a general approach for solving multimaterial problems with complex geometries and mixed Neumann-Dirichlet boundary conditions using neural networks. The implementation is publicly available in a GitHub repository (version v0.1.0). https://github.com/ShayanDodge/INI-VPINN}
}
```

## Paper and repository

For the formulation, derivation, benchmark definitions, and discussion of INI-VPINN, readers are strongly encouraged to read the paper:

- Paper: https://arxiv.org/abs/2606.18032
- Repository: https://github.com/ShayanDodge/INI-VPINN

If this repository is useful to your work, please consider **starring the GitHub repository** and citing the paper. This helps others discover the project and supports continued development.
