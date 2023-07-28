# Theory

## Background

The Vortex Lattice Method (VLM) is a numerical method used in computational fluid dynamics.
It is build on the Potential flow theory.
Although viscous effects and turbulence cannot be modelled explicitly by VLM, selected flows can be well approximated.
VLM allows to to estimate the aerodynamic force, composed of lift and induced drag, of an lifting surface such as aircraft's wing or sail.

## Potential flow theory

The potential flow theory treats external flows around bodies as incompressible, inviscid and irrotational {cite}`lecture` .
For small angle of attack, the fluid flow does not separate abruptly, and the viscous effects are limitted to a thin layer next to the body known as boundary layer.
In such case, the velocity field can be approximated by potential function.

The Laplace equation is the qoverning equation in the theory of potential flows: 

$$
\nabla^{2} \phi = 0
$$

where $\phi$ is a potentinal function of the velocity field.
It satisfies the conservation of mass and momentum.

## Vortex Lattice Method

In VLM, the lifting surface is modelled by a large number of elementary, quadrilateral panels lying either on the actual aircraft surface, or on some mean surface, or combination thereof. 
To satisfy boundary conditions, VLM utilizes following elements to describe each panel:

* source - a point from which fluid issues and flows radially outward such that the continuity equation is satisfied everywhere but at the singularity that exists at the source's center
* sink - a negative source
* doublet -  singularity resulting when a source or a sink of equal strength are made to approach each other such that the product of their strangths and their distance apart remains constant at a preselected finite value in the limit as a distance between them approaches zero
* vortex - an element that generates a circulation, or tangential motion, around its origin

Such singularities are defined by specifying functional variation across the panel and its value is set by determinating strength parameters. 
Such parameters are known after solving appropriate boundary condition equations.
When singularity strengts are determinated, the pressure, velocity can be computed{cite}`bertin`.

```{figure} ../../figures/panels.png
---
scale: 80%
name: panel-method
---
Representation of an airplane flowfield by panel (or singularity) methods. Figure taken from {cite}`bertin` (Fig. 7.22 page 350).
```

## Vortices

The vortex theorems for inviscid incompressible flows has been developed by German scientist Hermann von Helmholtz (1821-1894). The theory is based on the following assumptions {cite}`katz`:

* Flow is inviscid and incompressible
* The strength of vortex filament is constant along its length
* A vortex filament cannot start or end in a fluid (it must form or closed path or extend to infinity)
* The fluid that forms a vortex tube continues to form a vortex tube and the strength of the vortex tube remains constant as the tube moves about.

### Vortex element

Vortex element in 2D is presented on figure {numref}`{number} <vortex>`. 
It is created by placing a rotating cylindrical core in two dimentional flowfield. 
If the cylinder has a radius $R$ and a constant angular velocity of $\omega_y$, then its motion results in a flow with circular streamlines {cite}`katz`.

```{figure} ../../figures/vort.png
---
name: vortex
scale: 50%
---
Two dimentional flowfield around a cylindrical core rotating as a rigid body. Figure taken from {cite}`katz` (Fig. 2.11 page 34).
```

The tangential velocity, induced by the vortex, can be calculated as:

$$
\overrightarrow{w}_\theta(r) = \frac{\Gamma}{2\pi \cdot r}
$$

where $r$ is the distance from the vortex core.

If a vortex is located in free-stream with uniform velocity $u_\infty$, 
then the total velocity at the distance $r$ can be writtes as 
$\overrightarrow{u_\infty} + \overrightarrow{w}_\theta(r)$.

### Vortex segment

```{figure} ../../figures/vor_seg.png
---
name: vortex-segment
scale: 50%
---
Vortex segment in three dimentions. Figure taken from {cite}`katz` (Fig. 2.16 page 40).
```

The velocity induced at point $P(x,y,z)$ by a straight vortex segement of strength $\Gamma$ in three dimentions (figure {numref}`{number} <vortex-segment>`) is qiven by equation:

$$
\overrightarrow{w}_{1,2} = \frac{\Gamma}{4\pi}\frac{\overrightarrow{r}_{1} \times \overrightarrow{r}_{2}}{|\overrightarrow{r_1} \times \overrightarrow{r}_{2}|^2} \left(\frac{\overrightarrow{r}_{1}}{||\overrightarrow{r}_{1}||} - \frac{\overrightarrow{r}_{2}}{||\overrightarrow{r}_{2}||}\right) \cdot\overrightarrow{r}_{0}=\overrightarrow{\nu}\,\Gamma
$$ (q_finite)

where

$$
\overrightarrow{r}_{0} = \overrightarrow{r}_{1} - \overrightarrow{r}_{2}
$$

and

\begin{gather*}
\overrightarrow{r_{0}} = (x_2, y_2, z_2) - (x_1, y_1, z_1) \\
\overrightarrow{r_{1}} = P - (x_1, y_1, z_1)\\
\overrightarrow{r_{2}} = P - (x_2, y_2, z_2)
\end{gather*}

In case of a semi-infinite vortex line, the point 2 is infinitely far away thus formula simplifies {cite}`modern`:

$$
\overrightarrow{w}_{1,2} = \frac{\Gamma}{4\pi}\frac{\overrightarrow{u}_{\infty} \times \overrightarrow{r}_{1}}{||\overrightarrow{r}_{1}||(||\overrightarrow{r}_{1}|| - \overrightarrow{u}_{\infty} \cdot \overrightarrow{r}_{1})}=\overrightarrow{\nu}\,\Gamma
$$ (q_infinite)

## The Kutta Condition

The Kutta Condition states that at a small angle of attack the flow leaves the sharp trailing edge of an airfoil smoothly and the velocity is finite there {cite}`katz`. 
Because of this the normal component of velocity, from both sides of the airfoil, must vanish. 
Flow pattern with circulation consistent with the Kutta condition is shown on figure {numref}`{number} <kutta>`.

```{figure} ../../figures/kutta1.png
---
name: kutta
scale: 20%
---
Flow near cusped trailing edge. Upper figure: zero-lift flow around an airfoil. Lower figure: Upper and lower flows leave the trailing edge smoothly when Kutta condition is applied. Figure taken from {cite}`JohnDAnderson2007`.
```

### Lifting surface

```{figure} ../../figures/geom.png
---
height: 500
name: geoms
---
Sail coordinate system. Figure by author.
```

The coordinate system (CSYS) (see figure {numref}`{number} <geoms>`) is defined with the x-axis pointing backwards (towards stern), the y-axis in the transverse direction positive to starboard and the z-axis in spanwise direction positive upwards.

```{figure} ../../figures/siatka.png
---
name: siatka
height: 300px
---
Nomenclature of the lattice elements. Figure created by author.
```

The surface of the object is divided into panels (gray rectanges on figure {numref}`{number} <siatka>` ). 
The total amount of them is a product of spanwise and chordwise divisions. 
Vortex element is associated to segment one of the panel (pink rectangles).

There are two types of vortex elements:

* vortex ring
* vortex horseshoe

#### Vortex ring

```{figure} ../../figures/ring.png
---
height: 400
name: ring
---
Nomenclature of the vortex ring. Figure created by author.
```

Vortex ring (figure {numref}`{number} <ring>`) is created by four finite segments according to equation {eq}`q_finite`.

#### Horseshoe vortex

```{figure} ../../figures/horseshoe.png
---
height: 400
name: horseshoe
---
Nomenclature of the vortex horseshoe. Figure created by author.
```

Horseshoe vortex is attached to the trailing edge of lifting surface.
It consists of three finite and two semi-infinite segments following equation {eq}`q_finite` and {eq}`q_infinite` (see figure {numref}`{number} <horseshoe>`).

The bound vortex of the wing is considered bound to a "lifting line".  The lifting line theory considers the wing to be a single vortex filament.  The tip vortices are the "automatic" consequences of the lifting line and the circulation around a finite wing.

#### Vortex location

The center of pressure is a point to which a resulting aerodynamic force is attached.
It is located at the $1/4$ of a panel chord and at $1/2$ of the panel span (from panel leading edge). 
To fulfill no flow through the surface condition, the control point is defined at $3/4$ of the chord from the panel leading edge and in the middle of the span.

Vortex vertices $B_k$ and $C_k$ are placed at $1/4$ of panel chord ($v_{k}$), $A_k$ and $D_k$ at $1/4$ of the next panel ($v_{k+1}$). The panel opposite corner points define two vectors $\overrightarrow{A}_{k}$ and $\overrightarrow{B}_{k}$, and their vector product will point in the direction of $\overrightarrow{n}_{k}$ (normal vector).

### The Boundary Condition

The Boundary Condition requires no flow through the surface of the k-th panel:

$$
\overrightarrow{u_k} \cdot \overrightarrow{n_k} = 0  \Leftrightarrow \\ 
(\overrightarrow{u_{\infty}} + \overrightarrow{w_k}) \cdot \overrightarrow{n_k} = 0 \Leftrightarrow \\ 
(\overrightarrow{u_{\infty}} + \sum_j \overrightarrow{\nu_{kj}} \Gamma_j) \cdot \overrightarrow{n_k} = 0  \Leftrightarrow \\ 
\sum_j \overrightarrow{\nu_{kj}} \Gamma_j \cdot  \overrightarrow{n_k} = - \overrightarrow{u_{\infty}} \cdot \overrightarrow{n_k}
$$

Expanding...

$$
\underbrace{\overrightarrow{\nu_{11}} \cdot \overrightarrow{n_1}}_{a_{11}} \Gamma_1+
\underbrace{\overrightarrow{\nu_{12}} \cdot \overrightarrow{n_1}}_{a_{12}} \Gamma_2+
... +
\underbrace{\overrightarrow{\nu_{1N}} \cdot \overrightarrow{n_1}}_{a_{1N}} \Gamma_N+
=
\underbrace{- \overrightarrow{Q_{\infty}} \cdot \overrightarrow{n_1}}_{RHS_1}
\\
\underbrace{\overrightarrow{\nu_{21}} \cdot \overrightarrow{n_k}}_{a_{21}} \Gamma_1+
\underbrace{\overrightarrow{\nu_{22}} \cdot \overrightarrow{n_k}}_{a_{22}} \Gamma_2+
... +
\underbrace{\overrightarrow{\nu_{2N}} \cdot \overrightarrow{n_k}}_{a_{2N}} \Gamma_N+
=
\underbrace{- \overrightarrow{Q_{\infty}} \cdot \overrightarrow{n_k}}_{RHS_2}
$$

Which leads to a set of linear algebraic equations

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

where $m=n_{spanwise}\cdot\,n_{chordwise}$ and $a_{kj} = \overrightarrow{\nu_{kj}} n_k$

### The aerodynamic force

Once the system of equations is solved, and $\boldsymbol{\Gamma}$ is known,

$$
\boldsymbol{\Gamma} = \mathbb{A}^{-1} \boldsymbol{RHS}
$$

Then the aerodynamics force can be expressed according to the Kutta-Joukowski theorem,

$$
\overrightarrow{F}_{areo} = \rho \overrightarrow{u}_{\infty} \times \overrightarrow{b} \Gamma
$$

Where $\overrightarrow{b}$ is a span vector.

The aerodynamic force corresponding to the j-th section is:

$$
\overrightarrow{F_{j}}=\rho\,\overrightarrow{V}_{app\_wind\_fs\_j} \times \overrightarrow{b_j}\Gamma_{j} = \\
\rho(\overrightarrow{V}_{app\_wind\_infs\_j} + \overrightarrow{w}_{_j}) \times \overrightarrow{b_j}\Gamma_{j} = \\
\rho(\overrightarrow{V}_{app\_wind\_infs\_j} +
\sum{\overrightarrow{\nu_{jk}}\Gamma_{k}}) \times \overrightarrow{b_j}\Gamma_{j}
$$

where $b_j$ is a vector representing a finite vortex filement going through the center of pressure of the j-th section, $\overrightarrow{V}_{app\_wind\_infs\_j}$ is apparent wind velocity for an 'infinite sail' (without induced wind velocity) and $\overrightarrow{V}_{app\_wind\_fs\_j}$ is apparent wind velocity for a 'finite sail' (with induced wind velocity).

The pressure is computed as a normal component of a force divided by the area of a panel:

$$
p_k= \frac{\overrightarrow{F}_{k} \, \cdot \overrightarrow{n}_{k}}{S_k}
$$

Pressure coefficient at k-th panel follows the formula:

$$
c_p=\frac{p_k}{\frac{1}{2}\, \rho {\left|\left|\overrightarrow{u}_{\infty_k}\right|\right|}^2}
$$
<!---
Referencing do wyrazen matematycznych dziala w latexie, w htmlu nie, wiec rzeba tak pisac zdania zeby w latxie byly odnosniki a w html nie bylo to widoczne np tak jak w ostatnim wyrazeniu matematycznym{raw-latex}` \ref{eq:q12}`.
-->