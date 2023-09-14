# Convergence

pySailingVLM software allows user to specify the number of panels in a spanwise
and chordwise direction.
The more panels that are used during computations, the more precise solution will be obtained.
Below the rc44 example is used to show the total force per sail (Course over Ground) convergence.
The detailed program input values are describe in section {ref}`rc44py`. Geometry of a sails and rig is depicted in figure {numref}`{number} <rc44-fig>`. There is no leeway, heel is $13^\circ$ , yacht speed over ground is $3.446 \frac{m}{s}$ .
The true wind speed is $3.086 \frac{m}{s}$ with the angle of attack equal to 45 degrees. Simulations were performed sequentially for the following number of panels in spanwise direction per sail 6, 12, 24, 48, 96 and in chordwise direction: 2, 4, 8, 16, 32.


```{figure} ../../figures/fsx.png
---
width: 500px
name: fsx
---
$F\_sail\_total\_COG.x$ convergence. Figure created by author.
```

```{figure} ../../figures/fsy.png
---
width: 500px
name: fsy
---
$F\_sail\_total\_COG.y$ convergence. Figure created by author.
```

```{figure} ../../figures/fsz.png
---
width: 500px
name: fsz
---
$F\_sail\_total\_COG.z$ convergence. Figure created by author.
```

According to generated graphs, total force per sail (for all axises) converges to a certain value as the number of panels increases.


```{figure} ../../figures/drw_new.png
---
width: 500px
name: rc44-fig
---
Geometry of sails and rig. Mainsail girths and jib girts are horizontal, measured in meters and defined at percentage of the corresponding sail luff length of 0.25%
0.50% and 0.75%. Figure based on template from G. Gruszczyński.
```