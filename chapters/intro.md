# Project goals

## Sailing Vlm: Vortex Lattice Method for yacht geometry 

Sailing Vlm Project can help yacht hobbists to determinate optimal sail set geometry. Optimization of a set of sails, an inclined or bended mast as well as the heel or leeway of the boat is available.
User has to specify wind parameters and yacht geometry to allow computation. 

A vortex-lattice method (VLM) is used in this project.....

ten tekst pod spodem nie ma sensu, do przerobienia
An aeroelastic model has been developed to determine the elastic response of sailing yachts’ rigs and
sails due to the aerodynamic pressure induced on the sails by the wind. 
In the aeroelastic model, pressures are calculated using the VLM module and applied to the finite
element representation of the sail. Displacements are calculated and the new shape is used to
determine a new pressure distribution. The procedure is iterated until the pressure distribution has
converged. A comparison of a fixed and elastic rig is presented which shows the importance of using a
fully aeroelastic model when studying the behavior of yacht sails.
The VLM-implementation uses vortex ring elements with two different wake models: a fixed wake
aligned with the free-stream and a force free wake. The VLM-implementation shows good correlation
to commercial VLM-codes as well as with model tests. Results show minor differences between the
fixed- and the free wake model.
Three types of finite elements have been implemented to model the various parts of the rig: nonlinear
bar elements for stays and boom, nonlinear triangular membrane elements for sails and linear beam
elements for mast and spreaders. The Newton-Raphson method is used to solve the non-linear
structural problem for displacements. The structural implementation show good correlation to other
FEM-implementations and analytical solutions.

This is a small sample book to give you a feel for how book content is
structured.
It shows off a few of the major file types, as well as some sample content.
It does not go in-depth into any particular topic - check out [the Jupyter Book documentation](https://jupyterbook.org) for more information.

Check out the content pages bundled with this sample book to see more.

```{tableofcontents}
```
