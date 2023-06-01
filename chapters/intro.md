% for inserting raw code
```{role} raw-latex(raw)
:format: latex
```
# Abstract 

The beginning of fluid dynamics has started in acient Greece, when Archimedes investigated the fluid statics and bouancy. From that time, many well-konwn mathematicians and engineers have contributed to defining how air and gases behave. The equations they have constructed are extremely complex and difficult to calculate by hand when the geometry of airfoil is complicated. The rapid improvement of computers' power in 1970s has led to developing complex flow desings. Over the past few decades Computational Fluid Dynamics (CFD) has been improved dramatically. 

There are many methods, that are used in Computational Fluid Dynamics. Some of them are Finite Element Method (FEM), Volume of Fluid (VOF) and Lattice Boltzmann Method (LBM). They provide good and accurate results but require high amount of computational resources. To overcome this problem, low fidelity tools can be used, like Vortex Lattice Method (VLM). Using VLM is benefical in the early conceptual design phase {cite}`artphase`, when many different desings should be tested. Thanks to fast computations of aerodynamics forces and pressures, engineers can quickly overview modelled design performance.

In this work, we present the first open source Python package which implements Vortex Lattice Method for initial aerodynamic analysis of upwind sails. Thanks to its light weight requirements, the software can be immediately installed and execuded locally or accessed by cloud environment such as Google Collab. Additionally, package users can define own sail geometries and use pySailingVLM inside custom scripts which makes creating a set of dynamics very convenient.

Keywords: Vortex Lattice Method (VLM), initial sail analysis, yacht engineering, Python Package

Inside documentation:

```{tableofcontents}
```