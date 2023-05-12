% for inserting raw code
```{role} raw-latex(raw)
:format: latex
```
# Abstract 

The Vortex lattice method, also called VLM, is a numerical method used in computational fluid dynamics. VLM models a surface on aircraft as infinite vortices to estimate the lift curve slope, induced drag, and force distribution. The VLM is the extension of Prandtl's lifting-line theory that is capable of computing swept and low aspect ratio wings. {cite}`aac`. 

In this thesis, the method was used to determinate aerodynamic parameters such as CL, CD  and lift-to-drag ratio for modeling behaviour of sailing yacht with different initial wind conditions. 
The main purpose of this work was to update existing VLM code to be faster and more efficient. To achieve this goal authors have changed the structure of data and applied some compilations for specific functions in Python code using Numba which translates a subset of Python and NumPy code into fast machine code. Apart from this, the code has gained some bug fixes and new features such as cambered sail, pressure coefficient colormap, validation tests, command line script and jupyter notebook examples. Moreover, code has been packaged and now is available at The Python Package Index (PyPI) as a first open source python software designed for initial aerodynamic analysis of upwind sails. Thanks to its light weight requirements, the software can be immediately installed and executed locally or accessed through the web browser using cloud environment such as Google Collab. [#TODO pySailingVLM at PyPI](https://jupyterbook.org)

Keywords: Vortex Lattice Method, VLM, sailing, yacht, Python, code, visualisation, yacht engineering 

Inside documentation:

```{tableofcontents}
```
