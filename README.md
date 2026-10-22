# Projectile Motion Simulator: Ideal Motion vs Air Resistance

A Python simulation exploring how air resistance affects projectile motion and how numerical simulations compare with analytical predictions.

## Research Question

**How does quadratic air resistance change a projectile's trajectory, range and maximum height, and how accurately can numerical simulation reproduce ideal projectile motion?**

## Project Overview

This project compares three ways of modelling projectile motion:

- **Ideal analytical model:** calculates projectile motion using standard kinematic equations, assuming no air resistance.
- **Numerical model without air resistance:** simulates motion step by step and compares the results with the analytical solution.
- **Numerical model with quadratic air resistance:** incorporates drag to investigate how it changes the trajectory.

A numerical convergence test investigates how the simulation's time step affects the accuracy of its predictions.

## 1. Ideal Projectile Motion

The ideal model assumes that gravity is the only force acting on the projectile after launch. Air resistance is ignored.

The horizontal position is

$$
x(t)=v_0\cos(\theta)t
$$

The vertical position is

$$
y(t)=v_0\sin(\theta)t-\frac{1}{2}gt^2
$$

where:

- \(v_0\) is the initial speed, in metres per second (m/s).
- \(\theta\) is the launch angle measured from the horizontal.
- \(g\) is the acceleration due to gravity, in metres per second squared (m/s²).
- \(t\) is the elapsed time, in seconds.

For a projectile that lands at the same height from which it was launched, the theoretical range is

$$
R=\frac{v_0^2\sin(2\theta)}{g}
$$

The theoretical maximum height above the launch point is

$$
H=\frac{v_0^2\sin^2(\theta)}{2g}
$$

These equations provide reference values against which the numerical simulation can be compared.

## 2. Projectile Motion with Quadratic Air Resistance

In reality, a projectile moving through air experiences a drag force that opposes its velocity. This model uses quadratic drag, meaning that the magnitude of the drag force is proportional to the square of the speed.

The drag force is

$$
\mathbf{F}_d=-\frac{1}{2}\rho C_d A|\mathbf{v}|\mathbf{v}
$$

where:

- \(\rho\) is the density of air.
- \(C_d\) is the drag coefficient.
- \(A\) is the projectile's cross-sectional area.
- \(\mathbf{v}\) is the velocity vector.
- \(|\mathbf{v}|\) is the speed.
- The negative sign indicates that drag acts opposite to the direction of motion.

The projectile's acceleration is calculated using Newton's second law, including both gravity and air resistance.

Unlike the ideal model, the equations with quadratic drag are solved numerically because the changing velocity affects the drag force throughout the flight.

## 3. Numerical Method

The simulation uses the **semi-implicit Euler method** to update the projectile's velocity and position at small time intervals.

At each time step, the model calculates the acceleration, updates the velocity, and then updates the position. When the projectile reaches ground level, the simulation estimates its landing point using interpolation.

The time step, \(\Delta t\), determines how frequently the simulation updates the projectile's motion.

Smaller time steps generally improve the numerical approximation, although they require more calculations.

## 4. Constants and Parameters

| Parameter | Value | Unit |
|---|---:|---|
| Gravitational acceleration, \(g\) | 9.81 | m/s² |
| Air density, \(\rho\) | 1.225 | kg/m³ |
| Projectile mass, \(m\) | 0.145 | kg |
| Projectile radius, \(r\) | 0.037 | m |
| Drag coefficient, \(C_d\) | 0.47 | Dimensionless |
| Default time step, \(\Delta t\) | 0.01 | s |

The cross-sectional area is calculated using

$$
A=\pi r^2
$$

The initial speed and launch angle are entered when running the notebook.

## 5. Assumptions and Limitations

The simulation assumes:

- The projectile launches and lands at the same height.
- Gravitational acceleration remains constant.
- Air density and the drag coefficient remain constant.
- The projectile is spherical, with a fixed cross-sectional area.
- Air resistance acts opposite to the velocity.
- Wind, spin, lift and changes in air density are ignored.

The numerical model is an approximation. Its accuracy depends partly on the time step and the method used to estimate the landing point. The analytical equations apply only to the ideal model without air resistance.

## 6. Experiments and Validation

### Trajectory Comparison

The notebook plots the projectile's trajectory with and without air resistance.

Compare the two curves to investigate how drag changes the flight path, range and maximum height for the selected launch conditions.

### Numerical Convergence

The ideal numerical model is tested using time steps of 0.02 s, 0.01 s, 0.005 s and 0.001 s.

The simulated range and maximum height are compared with the corresponding analytical values using percentage error.

This experiment investigates whether reducing the time step improves agreement with the analytical solution.

## 7. Results

The notebook generates numerical results and graphs for the launch speed and angle entered at runtime.

The main outputs are:

- The theoretical range and maximum height from the ideal analytical model.
- The simulated range and maximum height.
- The trajectories with and without air resistance.
- The percentage errors for different time steps.
- A graph showing how numerical error changes as the time step decreases.

The numerical output should be used to draw conclusions about the effect of drag and the accuracy of the numerical method. The results will vary with the selected launch conditions.

## 8. Technologies Used

- **Python** — simulation and calculations.
- **NumPy** — numerical calculations and arrays.
- **Matplotlib** — trajectory and convergence graphs.
- **Jupyter Notebook** — code, explanations and results.

## 9. How to Run the Project

1. Install Python and Jupyter Notebook.
2. Install the required libraries:

   ```bash
   pip install numpy matplotlib
   ```

3. Open `Projectile_Motion_Simulator.ipynb` in Jupyter Notebook.
4. Run the cells in order.
5. Enter the initial speed and launch angle when prompted.
6. Examine the numerical output, trajectory plots and convergence results.

## Conclusion

This project investigates the differences between ideal projectile motion and motion affected by quadratic air resistance. It also tests the accuracy of numerical simulation by comparing results at different time steps with analytical predictions.

The simulation demonstrates how physical modelling and numerical methods can be combined to investigate a classical mechanics problem.

## Author

Swastik Mishra
