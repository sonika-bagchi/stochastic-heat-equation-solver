# Numerical Methods for Deterministic and Stochastic PDEs  
*A comprehensive progression from classical finite-difference schemes to stochastic PDEs and the incompressible Navier–Stokes equations*

This repository contains four Jupyter notebooks presenting a unified progression through numerical methods for partial differential equations (PDEs). The collection spans:

1. Deterministic 1D and 2D heat diffusion
2. The 1D linear advection equation
3. The 2D Poisson equation and the incompressible Navier–Stokes equations
4. Stochastic variants of the heat equation in 1D and 2D

Together, these notebooks illustrate foundational and advanced computational techniques used in applied mathematics, numerical analysis, and scientific computing.

---

# 1. Project Overview and Learning Progression

This repository is structured as a stepwise deepening of numerical PDE methods:

### **Stage A — Deterministic Parabolic PDEs**  
Finite difference solvers for the heat equation in 1D and 2D (explicit FTCS scheme).

### **Stage B — Hyperbolic PDEs**  
A solver for the 1D linear advection equation (central-difference scheme).

### **Stage C — Elliptic PDEs**  
A 2D Poisson solver using iterative relaxation (Gauss–Seidel), forming the basis of pressure solves in fluid dynamics.

### **Stage D — Incompressible Fluid Dynamics**  
A full finite-difference solver for the 2D incompressible Navier–Stokes equations using the projection (fractional-step) method.

### **Stage E — Stochastic PDEs**  
Explicit finite-difference solvers for the stochastic heat equation in 1D and 2D, incorporating random forcing.

This progression mirrors the trajectory of a graduate course in computational PDEs, illustrating methodological continuity from simple diffusion to nonlinear fluid flow and stochastic partial differential equations.

---

# 2. Deterministic Heat Equation (1D & 2D)

### **PDE:**
$u_t = \kappa u_{xx}$ (1D),  
$u_t = \kappa (u_{xx} + u_{yy})$ (2D).

### **Numerical Method:**
- Forward Euler in time
- Central differences in space
- 3-point (1D) and 5-point (2D) Laplacian stencils

### **Features:**
- Explicit stability condition: $dt \le dx^2 / (2\kappa)$
- Several initial conditions, including Gaussian pulses and fixed-temperature boundaries
- Visualizations including:
  - line plots,
  - heatmaps,
  - animated spatiotemporal solutions

---

# 3. 1D Linear Advection Equation

### **PDE:**
$u_t + c\,u_x = 0$

### **Numerical Method:**
Central differencing for $u_x$:

$u_i^{n+1} = u_i^n - c(dt / 2dx)(u_{i+1}^n - u_{i-1}^n)$.

### **Concepts demonstrated:**
- CFL stability: $|c|dt/dx \le 1$
- Numerical dispersion
- Behavior of hyperbolic PDEs under finite differences

This stage introduces hyperbolic transport, which also appears in the convective terms of the Navier–Stokes equations.

---

# 4. 2D Poisson Equation (Pressure Solve)

### **Equation:**
$\nabla^2 p = f(x,y)$

### **Method:**
- Gauss–Seidel relaxation
- Iterative convergence to elliptic PDE solutions
- Boundary enforcement on a rectangular grid

### **Purpose:**
This solver is used as the pressure-correction step in the projection method for incompressible flow.

---

# 5. 2D Incompressible Navier–Stokes Solver

### **PDE System:**
$u_t + (u\cdot\nabla)u = -p_x + \nu \nabla^2 u$  
$v_t + (u\cdot\nabla)v = -p_y + \nu \nabla^2 v$  
$u_x + v_y = 0$

### **Numerical Method: Projection (Fractional-Step) Scheme**

#### **1. Intermediate velocity (advection + diffusion):**

$u^\* = u^n + dt[-(u\cdot\nabla)u + \nu \nabla^2 u]$  
$v^\* = v^n + dt[-(u\cdot\nabla)v + \nu \nabla^2 v]$

#### **2. Pressure Poisson solve:**

$\nabla^2 p^{n+1} = (1/dt)(u^\*_x + v^\*_y)$

#### **3. Velocity correction:**

$u^{n+1} = u^\* - dt\,p_x$  
$v^{n+1} = v^\* - dt\,p_y$

### **Outputs include:**
- Pressure fields
- Velocity fields
- Streamlines and flow visualization

This solver demonstrates a complete incompressible fluid simulation in 2D.

---

# 6. Stochastic Heat Equation (1D & 2D)

### **PDE (1D):**
$u_t = \kappa u_{xx} + \sigma\,\eta(x,t)$

### **PDE (2D):**
$u_t = \kappa (u_{xx} + u_{yy}) + \sigma\,\eta(x,y,t)$

where $\eta$ denotes random forcing.

### **Implementation:**
- Same explicit FTCS deterministic update  
- Added stochastic term via random perturbations at each timestep  
- Animations showing sample-path evolution
- Adjustable noise amplitude and diffusion coefficient

### **Applications:**
- Stochastic PDE modeling
- Thermal fluctuations
- Random diffusion processes

These notebooks show how deterministic PDE solvers generalize naturally to stochastic settings.

---

# 7. Numerical Concepts Highlighted Across the Repository

- Finite difference discretization  
- Explicit time-marching schemes  
- Hyperbolic, parabolic, and elliptic PDE behavior  
- CFL stability constraints  
- Iterative solvers for elliptic PDEs  
- Pressure–velocity coupling in incompressible flow  
- Stochastic forcing in SPDEs  
- Visualization and diagnostics  

This breadth makes the repository an excellent demonstration of applied mathematical modeling and computational proficiency.

---

# 8. Running the Notebooks

### **Dependencies**
- Python 3.8+
- NumPy
- Matplotlib
- Jupyter Notebook
