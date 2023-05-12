# Theory

## Introduction
Vortex Lattice Method is build on the theory of ideal flow, known as Potential flow. Ideal flow is a simplication of the real flow which can be seen in nature. This  approximation is suffiecient from the engineering point of view. VLM do not take into account any turbulence, dissipation and viscous effects. 
## Potential flow theory
Potenttial Flow Theory treats external flows around bodies as invicid and irrational {cite}`lecture` .The viscous effects are limitted to a thin layer next to the body (boundary layer). Becouse of this and separation phenomena such fluid can be modelled only with small angle of attack. In irrational flow fluid particles are not rotating. 

In Potential Flow Theory, because velocity must satisfy the conservation of mass equation, the Laplace Equation is qoverning: 

$$
\nabla^{2} \phi = 0
$$

where $\phi$ is a potentinal function defined as continous function which satisfies the conservation of mass and momentum (incompressible, inviscid and irrational flow).
# Vortex Lattice method
The Vortex Lattice Method is a panel method where wing or other configuration is modelled by a large number of elementary, quadrilateral panels lying either on the actual aircraft surface, or on some mean surface, or combination thereof. Sources, vortices and doublets are attached to each panel. Such singularities are defined by specifying functional variation across the panel and its value is set by determinating strength parameters. Such parameters are known after solving appropriate boundary condition equations. When singularity strengts are determinated, the pressure, velocity can be computed{cite}`bertin`. 

```{figure} ../../figures/panels.png
---
scale: 80%
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

```{figure} ../../figures/vort.png
---
name: vortex
scale: 50%
---
Two dimentional flowfield around a cylindrical core rotating as a rigid body. Figure taken from {cite}`katz` (Fig. 2.11 page 34).
```

The tangential velocity induced is describe by equation:

$$
q_\theta(r) = \frac{\Gamma}{2\pi \cdot r}
$$

where $r$ is described as distance from the vortex.

If a vortex is located in free-strem with uniform velocity $u_\infty$ then the total velocity at the distance $r$ can be writtes as $u_\infty + q_\theta(r)$ {cite}`mgr`.

### Vortex segment
```{figure} ../../figures/vor_seg.png
---
name: vortex-segment
scale: 50%
---
Vortex segment in three dimentions. Figure taken from {cite}`katz` (Fig. 2.16 page 40).
```

The velocity induced by a straight vortex segement (figure {numref}`{number} <vortex-segment>`) in three dimentions with given vortex strength $\Gamma$ at point $P(x,y,z)$ is qiven by equation:

$$
\overrightarrow{q_{1,2}} = \frac{\Gamma}{4\pi}\frac{\overrightarrow{r_1} \times \overrightarrow{r_2}}{|\overrightarrow{r_1} \times \overrightarrow{r_2}|^2} \left(\frac{\overrightarrow{r_1}}{||\overrightarrow{r_1}||} - \frac{\overrightarrow{r_2}}{||\overrightarrow{r_2}||}\right) \cdot\overrightarrow{r_0}=\overrightarrow{\nu}\,\Gamma
$$ (q_finite)

where

$$
\overrightarrow{r_{0}} = \overrightarrow{r_1} - \overrightarrow{r_2}
$$

and 

\begin{gather*}
\overrightarrow{r_{0}} = (x_2, y_2, z_2) - (x_1, y_1, z_1) \\
\overrightarrow{r_{1}} = P - (x_1, y_1, z_1)\\
\overrightarrow{r_{2}} = P - (x_2, y_2, z_2)
\end{gather*}



In case of a semi-infinite vortex line, the point 2 is infinitely far away thus formula reads {cite}`modern`:

$$
\overrightarrow{q_{1,2}} = \frac{\Gamma}{4\pi}\frac{\overrightarrow{u_\infty} \times \overrightarrow{r_1}}{||\overrightarrow{r_1}||(||\overrightarrow{r_1}|| - \overrightarrow{u_\infty} \cdot \overrightarrow{r_1})}=\overrightarrow{\nu}\,\Gamma
$$ (q_infinite)

## The Kutta Condition
The Kutta Condition states that at small angle of attack the flow leaves the sharp trailing edge of an airfoil smoothly and the velocity is finite there {cite}`katz`. Because of this the normal component of velocity, from both sides of the airfoil, must vanish. Circulation at trailing edge can be expressed by equation:

$$
\gamma_{T.E.}=0
$$

```{figure} ../../figures/kutta.png
---
name: kutta
scale: 50%
---
Flow near cusped trailing edge. Figure taken from {cite}`katz` (Fig. 4.12 page 89)
```

## Lifting surface
```{figure} ../../figures/siatka.png
---
name: siatka
height: 300px
---
Nomenclature of the lattice elements.
```

### Grid Generation
The surface of the object is divided into panels (gray rectanges on figure {numref}`{number} <siatka>` ). The total amount of them is a product of number of panels spanwise and chordwise. Vortex element is associated to each one of them (pink rectangles). 

There are two types of vortex elements:
* vortex ring
* vortex horseshoe

```{figure} ../../figures/ring.png
---
height: 400
name: ring
---
Nomenclature of the vortex ring.
```

Vortex ring (figure {numref}`{number} <ring>`) is created by four finite segments according to equation {eq}`q_finite`. Horseshoe vortex is established by adding 3 finite and 2 infinite segments following equation {eq}`q_infinite` (see figure {numref}`{number} <horseshoe>`). By placing vortex at the quarter chord line of the the two-dimensional Kutta condition is satisfied along the chord.  Also, along the
wing trailing edges, the trailing vortex of the last panel row must be canceled to satisfy the three-dimensional trailing-edge condition

```{figure} ../../figures/horseshoe.png
---
height: 400
name: horseshoe
---
Nomenclature of the vortex horseshoe.
```

When thin surface is angled to a free-stream $u_{\infty}$, the aerodynamic force is being generated at center of pressure. This point is located at the $1/4$ of a panel chord and at $1/2$ of the panel span (from panel leading edge). To fulfill no flow through the surface, the control point is defined at $3/4$ of the chord from the panel leading edge and in the middle of the span.

Vortex vertices $B_k$ and $C_k$ are placed at $1/4$ of panel chord ($v_{k}$), $A_k$ and $D_k$ at $1/4$ of the next panel ($v_{k+1}$). The panel opposite corner points define two vectors $\overrightarrow{A_k}$ and $\overrightarrow{B_k}$, and their vector product will point in the direction of $\overrightarrow{n_k}$ (normal vector).


### Computations

To converse  which claims that there should be  of the k-th panel, the equation below is set:

If the velocity induced at k-th panel is $\overrightarrow{q_{ind}}$, no flow through the surface (boundary condition) is fulfield when:

$$
(\overrightarrow{u_{\infty}} + \overrightarrow{q_{ind}})\cdot\,\overrightarrow{n_k}=0
$$ (bc)

After equation transformation:

$$
\sum_{j} \underbrace{\overrightarrow{\nu_{kj}}\,\Gamma_j}_{a_{kj}} \cdot \overrightarrow{n_k}=-\overrightarrow{u_{\infty}}\,\cdot\,\overrightarrow{n_k}
$$ (bc2)

By expanding equation {eq}`bc` and {eq}`bc2` the RHS coefficient vector can be computed:

$$
RHS_k=-\overrightarrow{u_{\infty}}\,\cdot\overrightarrow{n_k}
$$

In arder to obtain gamma magnitude at k-th panel, the following set of algebraic equations must be solved.
\begin{gather}
    \begin{bmatrix} 
    a_{11} & \dots  & a_{1m}\\
    \vdots & \ddots & \vdots\\
    a_{m1} & \dots  & a_{mm}
    \end{bmatrix}
\begin{bmatrix} 
    \Gamma_{1} \\
    \vdots \\
    \Gamma_{m}
    \end{bmatrix}
 =
  \begin{bmatrix} 
    RHS_{1} \\
    \vdots \\
    RHS_{m}
    \end{bmatrix}
\end{gather}

where $m=n_{spanwise}\cdot\,n_{chordwise}$.


The force can be expressed according to the Kutta-Joukowski theorem as:

$$
\overrightarrow{F_{k}}=\rho\,\overrightarrow{u_{\infty_{k}}}\,\Gamma_k\, b_k
$$

where $b_k$ is a span of k-th panel, which is placed at k-th control point. 
Lift is defined as the component of the aerodynamic force that is perpendicular to the flow direction and can is defined as a dot product of force and normal vector:

$$
L_k=\overrightarrow{F_k}\,\cdot \overrightarrow{n_k}
$$

Pressure at k-th panel:

$$
p_k=\frac{L_k}{S_k}
$$


Pressure coefficient at k-th panel can be defined as:

$$
c_p=\frac{p_k}{\frac{1}{2}\, \rho {\left|\left|\overrightarrow{u_{\infty_k}}\right|\right|}^2}
$$
<!---
Referencing do wyrazen matematycznych dziala w latexie, w htmlu nie, wiec rzeba tak pisac zdania zeby w latxie byly odnosniki a w html nie bylo to widoczne np tak jak w ostatnim wyrazeniu matematycznym{raw-latex}` \ref{eq:q12}`.
-->