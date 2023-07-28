# Technology

The initial version of pySailingVLM has been implemented in a Object Oriented (OO) way. 
Each panel has been represented by an instance of an object.
Every one of them had many atributtes like cooridinates, force, pressure, pressure coefficient, span, normal vector, etc.
Such arrangment is refereed as Array of Structures (AoS).

To speed up the program, the Numba library has been employed.
It provides a JIT (just in time) compiler which can complile the regular python script into a machine code.
Moreover, parallel calculations for SIMD (single instruction multiple data) can be automatically applied.
Unfortunately, Numba can not handle custom objects like panel.
Therefore, the code has been rewritten to store the aforementioned attibutes as independend arrays instead of keeping them within objects.

## Memory layout

Array of Structures (AoS) and Structure of Arrays (SoA) are layouts arranging a sequence of records in memory.
Structure of Arrays (SoA) layout splits elements of a record into separate vectors of a given type, allowing coalesced memory access.
The AoS is the opposite layout.
It is a collection of structures where each structure contains different records.
Comparison between conceptual layout and memory layout is shown on figure {numref}`{number} <memory_layout>`.

```{figure} ../../figures/memory_layout.png
---
height: 300
name: memory_layout
---
Comparison of the Structure of Arrays (SoA) and Arrray of Structure (AoS). Figure 2 from {cite}`opencl`
```

The AoS approach ensures that the five values $a_i, b_i, c_i, d_i, e_i$ are next to one another in memory,
providing good cache utilisation.
The SoA approach makes sure that these values are split into five separate units, allowing access to corresponding elements in parallel {cite}`opencl`.

Simple values like pressure coefficients, forces, pressure acting on each panel were arranged into simple NumPy arrays (SoA). Panel coorditnates, span and normal vectors were kept as nested ones (AoS).
Figure {numref}`{number} <uklad>` shows data layout implemented.

```{figure} ../../figures/panele.drawio.png
---
height: 600
name: uklad
---
Data layout implemented in pySailingVLM. Figure created by author.
```

## Benchmarks

To benchmark pySalingVLM, the time comparison tests were conducted. Three approaches was summaries in the table {numref}`{number} <benchs>`: object oriented (OO) code, functional (FP) approach, object oriented with Numba and functional code compiled with Numba.  The tests were carried out on a laptop with the following parameters: AMD Ryzen 7 4800H with 8 CPU cores (16 threads), base clock: 2.9 GHz, max boost: 4.2GHz, 32 GB RAM. For 1600 panels more then thirty times acceleration was obtained.

```{list-table} Time execution comparison between different approaches of implementing pySailingVLM depending on sail shape.
:header-rows: 1
:name: benchs

* - No. panels
  - OO [s]
  -  FP [s]
  - OO + Numba [s]
  - FP + Numba [s]
* - 100
  - 16.51
  - 20.0
  - 1.71
  - 1.04
* - 400
  - 269.13
  - 301.39
  - 21.81
  - 10.41
* - 600
  - 593.85
  - 647.96
  - 48.44
  - 22.51
* - 1600
  - 4325.78
  - 4458.05
  - 320.54
  - 143.69
* - 2400
  - no data
  - no data
  - 724.70
  - 320.12
* - 3600    
  - no data
  - no data
  - 1653.52
  - 706.62
```

According to time results, using Numba is much more efficient when applied to the functional code. In order to explain such behaviour the SIMD term should be investigated.

### SIMD and vectorization

SIMD stands for Single Instruction Multiple Data. Instead of performing a single instruction on every single data, SIMD uses wider data-width for similar computational operations {cite}`simd`. A comparison between simple scalar operation and a SIMD computation is depicted in figure {numref}`{number} <simd_fig>`.

```{figure} ../../figures/simd_fig.png
---
height: 200
name: simd_fig
---
Simple scalar operation (a) and a SIMD computation (b). Figure 1 from {cite}`simd`.
```

Vectorization with AOS in memory data layout requires multiple load/shuffle/insert or gather instructions. Because of the reduced CPU frequency in SIMD mode its improvements are not sufficient. Increase in vector width demands more instructions for vector construction. A properly aligned memory data layout for vectorization which Numba uses, needs Structure of Arrays (SOA). It provides SIMD compatible memory accesses and results in efficiency and speedup {cite}`intel`.

### Programming paradigms

Object Oriented and functional programming paradigms take a very different approach to how code is structured. In Object Oriented code objects are used to represent data, functions or methods are used to manipulate the given object {cite}`medium`. This apprach is used to perform a few operations with common behavior and different variants {cite}`educba`.

Functional programming uses functions for creating clean and maintainable software {cite}`infoworld`. FP should rely on pure functions which given the same inputs, always returns the same output and does not have any side effects. Side effects appears when function relies on, modifies, something outside its parameters to do something (e.g. function doing IO operations) {cite}`yld`. Functional programming provides high performance in processing large data for applications {cite}`educba`.

According to table {numref}`{number} <benchs>` pySailingVLM functional code is a little bit lower than Object Oriented approach. FP code implementation can gain some improvements to achieve better results:

* reducing the number of local variables inside functions
* vectorizing for-loops using np.vectorize() function from Numpy module
* change the Numpy array initialization method: np.zeros() -> np.empty()

## Other improvements

Apart from code optimizations, the pySailingVLM has gained more features. 
The possibility to calculate cambered sails and visualize pressure coefficients on colormap was introduced. 
Code has been packaged and now is available at Python Package Index (PyPI). 
It can be run locally from command line or in a cloud using Jupyter Notebook. 
pySailingVLM can be executed in a user defined script, which make it easy to calculate and compare many sailing cases.
