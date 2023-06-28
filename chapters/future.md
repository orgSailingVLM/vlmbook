# Future outlooks

Some improvements to pySailingVLM code can be conducted in order to decrease program time execution. 
##  GPU
Apart form CPU programing, Numba supports CUDA GPU programming by directly compiling a restricted subset of Python code into CUDA kernels and device functions using the CUDA execution model. Kernels which are written in Numba appear to have direct access to NumPy arrays according to documantation {cite}`numba`. The NumPy arrays are automatically shifted between the CPU and the GPU. To increase code performance, calcuations can be moved to GPU. 

## All code as SoA
Up to now, most of Python objects are represented as Structure of Arrays, except panels. To take full adventage of GPU speed up, panels can be rewriten into SoA. This memory layout is recommended for CUDA acceleration {cite}`intel` due to parallel acces to data units.

## Points dupllicate

Panels which are close to each other share same points (see figure {numref}`{number} <future_panels>`). Current pySailingVLM implementation do not take into account this fact and there are duplicates of points coordinates in panel array. Reducing redundant points can improve the code efficiency.
```{figure} ../figures/future_drawio.png
---
height: 500
name: future_panels
---
Points on panels arragement. Figure created by author.
```

## Automatic Differentiation
pySailingVLM code can be extended to provide an option to find the best sail shape for the given wind conditions. 
??????????????????????????????????????????????????????????????????????????????? 
co tu dopisac?????