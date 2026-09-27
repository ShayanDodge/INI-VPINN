# INI-VPINN

**A Variational Physics-Informed Neural Network with Implicit Neumann and Interface Handling for Multi-Material Domains with Geometric Singularities**

**Authors:** Shayan Dodge, Alessandro Formisano, Sami Barmada  
**Journal:** *Journal of Computational Physics (JCP)*  
**DOI:** `10.1016/j.jcp.2026.115328`

The INI-VPINN paper is published in the **Journal of Computational Physics (JCP)**.

This repository hosts the public INI-VPINN implementation and will be expanded progressively with the benchmark cases presented in the work.

## Release Status

### v1.0.0 — Homogeneous inverted-T benchmark

The first public release, **v1.0.0**, provides the **homogeneous inverted-T benchmark** with:

- the complete INI-VPINN training notebook;
- operator-guided element-wise test-function selection;
- Gauss-Lobatto-Jacobi quadrature;
- FEM reference data and validation;
- prediction and error-history outputs;
- publication-ready comparison and convergence plots.

The main notebook is:

```text
INI_VPINN_v1.0.0_Homogeneous.ipynb
```

### Coming next

The repository will be extended with additional INI-VPINN cases, including:

- **non-homogeneous boundary-condition benchmarks**;
- **Poisson-equation benchmarks**;
- **non-rectangular geometries** and additional geometric-singularity cases.

These examples are currently being prepared and will be published in future versions of this repository.

## Code Availability

Thank you for your interest in **INI-VPINN**.

The first clean and documented implementation is now available through the **v1.0.0 homogeneous inverted-T release**. Additional examples and benchmark configurations will be added progressively to support reproducibility and broader use of the method.

For the mathematical formulation, weak-form derivation, implicit treatment of Neumann/interface conditions, and benchmark definitions, readers are strongly encouraged to read the paper.

- **Paper:** https://doi.org/10.1016/j.jcp.2026.115328
- **Repository:** https://github.com/ShayanDodge/INI-VPINN

If INI-VPINN is useful for your work, please ⭐ **star this repository** and cite the paper. This helps others discover the project and supports future releases.

---

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
