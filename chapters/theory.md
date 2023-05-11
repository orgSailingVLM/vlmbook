# Theory

## Introduction
Vortex Lattice Method is build on the theory of ideal flow, known as Potential flow. Ideal flow is a simplication of the real flow which can be seen in nature. This  approximation is suffiecient from the engineering point of view. VLM do not take into account any turbulence, dissipation and viscous effects. 
## Potential flow theory
Potenttial Flow Theory treats external flows around bodies as invicid and irrational {cite}`lecture` .The viscous effects are limitted to a thin layer next to the body (boundary layer). Becouse of this and separation phenomena such fluid can be modelled only with small angle of attack. In irrational flow fluid particles are not rotating. 

In Potential Flow Theory, because velocity must satisfy the conservation of mass equation, the Laplace Equation is qoverning: 

\begin{equation}
\label{nabla}
\nabla^{2} \phi = 0
\end{equation}

where $\phi$ is a potentinal function defined as continous function which satisfies the conservation of mass and momentum (incompressible, inviscid and irrational flow).
# Vortex Lattice method
The Vortex Lattice Method is a panel method where wing or other configuration is modelled by a large number of elementary, quadrilateral panels lying either on the actual aircraft surface, or on some mean surface, or combination thereof. Sources, vortices and doublets are attached to each panel. Such singularities are defined by specifying functional variation across the panel and its value is set by determinating strength parameters. Such parameters are known after solving appropriate boundary condition equations. When singularity strengts are determinated, the pressure, velocity can be computed{cite}`bertin`. 

```{figure} ../figures/panels.png
---
height: 250px
name: panel-method
---
Representation of an airplane flowfield by panel (or singularity) methods. Figure taken from {cite}`bertin` (Fig. 7.22 page 350).
```

## Vortices
Element which creates circulation around its origin is called a vortex. According to German scientist Hermann von Helmholtz who developed vortex theorems for inviscid incompressible flows {cite}`katz`:
* The strength of vortex filament is constant along its length
* A vortex filament cannot start or end in a fluid (it must form or closed path or extend to infinity)
* The fluid that forms a vortex tube continues to form a vortex tube and the strength of the vortex tube remains constant as the tube moves about.

### Vortex element
Vortex element in 2D is presented on figure {numref}`{number} <vortex>`. It is created by placing a rotating cylindrical core in two dimentional flowfield. If the cylinder has a radius $R$ and a constant angular velocity of $\omega_y$, then its motion results in a flow with circular streamlines {cite}`katz`.

```{figure} ../figures/vort.png
---
name: vortex
scale: 100%
---
Two dimentional flowfield around a cylindrical core rotating as a rigid body. Figure taken from {cite}`katz` (Fig. 2.11 page 34).
```

The tangential velocity induced is describe by equation:

\begin{equation}
\label{q_theta}
q_\theta(r) = \frac{\Gamma}{2\pi \cdot r}
\end{equation}

where $r$ is described as distance from the vortex.

If a vortex is located in free-strem with uniform velocity $u_\infty$ then the total velocity at the distance $r$ can be writtes as $u_\infty + q_\theta(r)$ {cite}`mgr`.

### Vortex segment
```{figure} ../figures/vor_seg.png
---
name: vortex-segment
scale: 100%
---
Vortex segment in three dimentions. Figure taken from {cite}`katz` (Fig. 2.16 page 40).
```

The velocity induced by a straight vortex segement (figure {numref}`{number} <vortex-segment>`) in three dimentions with given vortex strength $\Gamma$ at point $P(x,y,z)$ is qiven by equation:

\begin{equation}
\label{eq:q12}
q_{1,2} = \frac{\Gamma}{4\pi}\frac{\overrightarrow{r_1} \times \overrightarrow{r_2}}{|\overrightarrow{r_1} \times \overrightarrow{r_2}|^2} \left(\frac{\overrightarrow{r_1}}{||\overrightarrow{r_1}||} - \frac{\overrightarrow{r_2}}{||\overrightarrow{r_2}||}\right) \cdot\overrightarrow{r_0}
\end{equation}

where

\begin{equation}
\overrightarrow{r_{0}} = \overrightarrow{r_1} - \overrightarrow{r_2}
\end{equation}

and 

\begin{gather}
\overrightarrow{r_{0}} = (x_2, y_2, z_2) - (x_1, y_1, z_1) \\
\overrightarrow{r_{1}} = P - (x_1, y_1, z_1)\\
\overrightarrow{r_{2}} = P - (x_2, y_2, z_2)
\end{gather}

In case of a semi-infinite vortex line, the point 2 is infinitely far away thus formula reads {cite}`modern`:

\begin{equation}
\label{q12_inf}
q_{1,2} = \frac{\Gamma}{4\pi}\frac{\overrightarrow{u_\infty} \times \overrightarrow{r_1}}{||\overrightarrow{r_1}||(||\overrightarrow{r_1}|| - \overrightarrow{u_\infty} \cdot \overrightarrow{r_1})} 
\end{equation}




Referencing do wyrazen matematycznych dziala w latexie, w htmlu nie, wiec rzeba tak pisac zdania zeby w latxie byly odnosniki a w html nie bylo to widoczne np tak jak w ostatnim wyrazeniu matematycznym{raw-latex}` \ref{eq:q12}`.