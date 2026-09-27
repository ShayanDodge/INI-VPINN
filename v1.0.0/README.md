# INI-VPINN v1.0.0

Homogeneous inverted-T benchmark for **INI-VPINN**.

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

For the supplied homogeneous inverted-T case:

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

> Shayan Dodge et al., **“INI-VPINN: A Variational Physics-Informed Neural Network with Implicit Neumann and Interface Handling for Multi-Material Domains with Geometric Singularities,”** arXiv:2606.18032, 2026.

BibTeX:

```bibtex
@article{dodge2026inivpinn,
  title   = {INI-VPINN: A Variational Physics-Informed Neural Network with Implicit Neumann and Interface Handling for Multi-Material Domains with Geometric Singularities},
  author  = {Dodge, Shayan and others},
  journal = {arXiv preprint arXiv:2606.18032},
  year    = {2026}
}
```

## Paper and repository

For the formulation, derivation, benchmark definitions, and discussion of INI-VPINN, readers are strongly encouraged to read the paper:

- Paper: https://arxiv.org/abs/2606.18032
- Repository: https://github.com/ShayanDodge/INI-VPINN

If this repository is useful to your work, please consider **starring the GitHub repository** and citing the paper. This helps others discover the project and supports continued development.
