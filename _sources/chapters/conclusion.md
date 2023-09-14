# Summary

```{note}

**pySailingVLM**

- python package for initial aerodynamic analysis of upwind sails
- for early stage design (run < 1min)
- upwind sails only (no separation, no viscous drag)
- easy to install & run locally or in a cloud environment (e.g. Binder)

```

The pySailingVLM package is created for initial aerodynamic analysis of upwind sails in conceptual phase, when variety of different desings are tested.
The functional code has been compiled with Numba, allowing for substantial acceleration of the program.
Th results obtained by pySailingVLM have been sucesfully benchmarked using theoretical formulas and other software {cite}`mgr`.
The package has lightweight requirements and can be run locally or in a cloud environment such as Binder.
Users are invited to define their own sail geometries and visualize the results.
