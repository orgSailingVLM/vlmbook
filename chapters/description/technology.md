# Technology

The main purpose of the thesis was to optimize the existing code for initial sail analysis. The surface of the geometry used is defined with coordinates in three dimensions (figure {numref}`{number} <geom>`)  with the x-axis in the yachts longitudinal (chordwise) direction positivevbackwards, the y-axis in the transverse direction positive to starboard and the z-axis in spanwise direction positive upwards. 

```{figure} ../../figures/geom.png
---
height: 400
name: geom
---
Discretization of jib sail into 3 chordwise and 7 spanwise panels each. Figure created by author.
```

Orginally the code was written in pure OPP (Object Oriented Programming) Python which led to time consuming computations. To solve this problem, the code was rewritten in a non-objective way. Figure {numref}`{number} <uklad>` shows data layout implemented. Insted of creating many Python objects, data such as coordinates of panels, pressure coefficients were arranged into sets of arrays. Thanks to this, the code has become less complicated and the  Numba (a JIT compiler that translates Python code and NumPy into machine code) enabled parallel coalcuations.

```{figure} ../../figures/panele.drawio.png
---
height: 400
name: uklad
---
Data layout implemented in pySailingVLM. Figure created by author.
```
To benchmark pySalingVLM, the time comparison tests were conducted. Three approaches was summaries in the table {numref}`{number} <benchs>`: objective code, objective code with Numba and non-objective compiled with Numba.  The tests were carried out on a laptop with the following parameters: AMD Ryzen 7 4800H with Radeon, 2.9 GHz, 32 GB RAM, Nvidia GeForce graphics card GTX 1650. For 20x20 shape more then thirty times acceleration was obtained.

```{list-table} Time execution comparison between different approaches of implementing pySailingVLM depending on sail shape.
:header-rows: 1
:name: benchs

* - $n_{spanwise}\times\,n_{chordwise}$
  - objective [s]
  - objective + numba [s]
  - non-objective + numba [s]
* - 5x5
  - 16.51
  - 1.71
  - 1.04
* - 10x10
  - 269.13
  - 21.81
  - 10.41
* - 15x10
  - 593.85
  - 48.44
  - 22.51
* - 20x20
  - 4325.78
  - 320.54
  - 143.69
* - 30x20
  - no data
  - 724.70
  - 320.12
* - 30x30    
  - no data
  - 1653.52
  - 706.62
```
Moreover, the Vortex Lattice Method implementation was improved: the horseshoe vortex was introduced and is used at trailing edge (insted of vortex ring). New approach has added possibility to calculate cambered sailis and visualize pressure coefficients on colormap. Code has been packaged and now is available at PyPi. It can be run locally from command line or in a cloud using Jupyter Notebook. pySailingVLM can be executed in a user defined script, which make it easy to calculate and compare many sailing cases.
