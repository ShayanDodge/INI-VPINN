# INI-VPINN

**A Variational Physics-Informed Neural Network with Implicit Neumann and Interface Handling for Multi-Material Domains with Geometric Singularities**

**Authors:** Shayan Dodge, Alessandro Formisano, Sami Barmada  
**Journal:** *Journal of Computational Physics (JCP)*  
**DOI:** `10.1016/j.jcp.2026.115328`    
**Links:**  [ScienceDirect](https://doi.org/10.1016/j.jcp.2026.115328) ·[arXiv](https://arxiv.org/abs/2606.18032) ·[ResearchGate](https://www.researchgate.net/publication/413656372_INI-VPINN_A_Variational_Physics-Informed_Neural_Network_with_Implicit_Neumann_and_Interface_Handling_for_Multi-Material_Domains_with_Geometric_Singularities)

The INI-VPINN paper is published in the **Journal of Computational Physics (JCP)**.

This repository hosts the public INI-VPINN implementation and will be expanded progressively with the benchmark cases presented in the work.

## Release Status

### v1.0.0 — Homogeneous inverted-T benchmark

The first public release, **v1.0.0**, provides the **homogeneous inverted-T benchmark** with:

- the complete INI-VPINN training notebook;
- operator-guided element-wise test-function selection;
- FEM reference data and validation;
- prediction and error-history outputs;
- publication-ready comparison and convergence plots.

The main notebook is:

```text
INI_VPINN_v1.0.0_Homogeneous.ipynb
```

### Coming next

The repository will be extended with additional INI-VPINN cases, including:

- **Non-Homogeneous doman benchmarks**;
- **Poisson-equation benchmarks**;
- **Non-Rectangular geometries**.

These examples are currently being prepared and will be published in future versions of this repository.

## Code Availability

Thank you for your interest in **INI-VPINN**.

The first clean and documented implementation is now available through the **v1.0.0**. Additional examples and benchmark configurations will be added progressively to support reproducibility and broader use of the method.

For the mathematical formulation, weak-form derivation, implicit treatment of Neumann/interface conditions, and benchmark definitions, readers are strongly encouraged to read the paper.

- **Paper:** https://doi.org/10.1016/j.jcp.2026.115328
- **Repository:** https://github.com/ShayanDodge/INI-VPINN

If INI-VPINN is useful for your work, please ⭐ **star this repository** and cite the paper. This helps others discover the project and supports future releases.


