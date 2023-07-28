# Abstract

Nowadays, the state-of-the-art CFD solvers (FEM, VOF, LBM) can provide incredibly accurate results for almost any geometry.
However, the solution comes at the price of high amount of computational resources.
To circumvent this issue, the low fidelity approaches like Vortex Lattice Method (VLM){cite}`artphase` can be employed for particular types of computational problems.
The VLM is an engineering standard in the conceptual design phase of aircrafts or sailing yachts as it allows designers to quickly estimate the performance of numerous different models.
Due to the specifics of conditions in which a sailing yacht operates, the VLM solvers dedicated to aircraft design can not be adopted in a straightforward fashion.
Here, we present the first open-source Python package which implements the
Vortex Lattice Method for the initial aerodynamic analysis of upwind sails. Thanks to its lightweight requirements, the software can be easily installed and executed locally or accessed in a cloud environment such as Binder.

```{note}

**pySailingVLM** is available at

    https://pypi.org/project/pySailingVLM/
    https://github.com/orgSailingVLM/pySailingVLM
    
```

**Keywords**: Vortex Lattice Method (VLM), initial sail analysis, yacht engineering, python package

## Table of contents

```{tableofcontents}
```
