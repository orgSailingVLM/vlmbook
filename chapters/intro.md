% for inserting raw code
```{role} raw-latex(raw)
:format: latex
```
# Abstract 

The beginning of fluid dynamics has started in acient Greece, when Archimedes investigated the fluid statics and bouancy. From that time, many well-konwn mathematicians and engineers have contributed to defining how air and gases behave. The equations they have constructed are extremely complex and difficult to calculate by hand when the geometry of airfoil is complicated. The rapid improvement of computers' power in 1970s has led to developing complex flow desings. Over the past few decades CFD has been improved dramatically. 

There are many methods, that are used in Computational Fluid Dynamics. Some of them are Finite Element Method (FEM), Volume of Fluid (VOF) and Lattice Boltzmann Method (LBM). They provide good and accurate results but require high amount of computational resources. To overcome this problem, low fidelity tools can be used, like Vortex Lattice Method (VLM). Using VLM is benefical in the early conceptual design phase, when many different desings should be tested. Thanks to fast computations of aerodynamics forces and pressures, engineers can quickly overview modelled design performance.

In this work, we present the first open source Python package which implements Vortex Lattice Method for initial aerodynamic analysis of upwind sails. Thanks to its light weight requirements, the software can be immediately installed and execude locally or accessed by cloud environment such as Google Collab.


# file:///home/zuzanna/Downloads/754-Article%20Text-3598-2-10-20210329.pdf
# https://www.dive-solutions.de/blog/cfd-methods
the ability of multi evaluate? tion? multi-potentional designs 


good results but require high amount of computational resources 

some simplified methods are used like VLM
there we will focus on VLM, which is known from II w s

#TODO move to theory
The Vortex Lattice Method (VLM) is a numerical method used in computational fluid dynamics. VLM models a surface on aircraft as infinite vortices to estimate the lift curve slope, induced drag, and force distribution. The VLM is the extension of Prandtl's lifting-line theory that is capable of computing swept and low aspect ratio wings. {cite}`aac`. 

In this thesis, the method was used to determinate aerodynamic parameters such as CL, CD  and lift-to-drag ratio for modeling behaviour of sailing yacht with different initial wind conditions. 
The main purpose of this work was to update existing VLM code to be faster and more efficient. To achieve this goal authors have changed the structure of data and applied some compilations for specific functions in Python code using Numba which translates a subset of Python and NumPy code into fast machine code. Apart from this, the code has gained some bug fixes and new features such as cambered sail, pressure coefficient colormap, validation tests, command line script and jupyter notebook examples. Moreover, code has been packaged and now is available at The Python Package Index (PyPI) as a first open source python software designed for initial aerodynamic analysis of upwind sails. Thanks to its light weight requirements, the software can be immediately installed and executed locally or accessed through the web browser using cloud environment such as Google Collab. [#TODO pySailingVLM at PyPI](https://jupyterbook.org)

Keywords: Vortex Lattice Method, VLM, sailing, yacht, Python, code, visualisation, yacht engineering 

Inside documentation:

```{tableofcontents}
```
