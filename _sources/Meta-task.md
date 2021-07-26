# Meta-task

## A comprehensive approach: by [Coetzee et al.](https://www.sciencedirect.com/science/article/pii/S0032591017300268) and [Katterfeld et al.](https://www.researchgate.net/profile/Andre_Katterfeld/publication/334129169_Calibration_of_DEM_Parameters_for_Cohesionless_Bulk_Materials_under_Rapid_Flow_Conditions_and_Low_Consolidation/links/5d26670792851cf440789112/Calibration-of-DEM-Parameters-for-Cohesionless-Bulk-Materials-under-Rapid-Flow-Conditions-and-Low-Consolidation.pdf) to calibrate DEM parameters for cohesionless materials

This is a calibration workflow that executes simulations in a specific order to isolate certain parameters.

### 1. Particle size and shape

Select a model for the particle **shape**.

- Using a single sphere.
- Using *clumps*/*Multi-spheres* -one can use optimization software to create clumps after scanning particles, to most accurately represent particle size and shape-.
- By special mathematical descriptions of non-spherical particles:
  - using superquadric equations
  - polyhedrons
  - faceted particles (e.g., created from imported STL models)

> **Note**: The particle shape will influence all the other calibrated values, and if the adjusted shape is changed, the calibrated values should all be re-calibrated.

The particle **size** distribution, should be specified based on the application, computation power, size of calibration experiments as well as the time constraints.

> **Note**: The particle size and shape affects the packing porosity and consequently the bulk density.

### 2. Select/measure coefficient of restitution

It can be measured by **drop tests**. Since a stream of bulk materials usually show a rather strong damping behavior, selecting a value between 0.2-0.4 will reduce the parameters to be calibrated.

> **Note**: This should be done for each type of contact/material.

### 3. Particle-wall friction coefficient

In this calibration method, sliding and rolling friction (rolling for spherical particles) are simply measured by an **inclined plane test** or **wall shear test**.

> **Note**: the still not calibrated parameters -especially **particle density** and **particle-particle friction** should have realistic values.

### 4. Particle stiffness calibration

Particle stiffness calibration is performed by performing an **uniaxial compression test**.

The relation between *the particle stiffness* and *the bulk stiffness* is linear, and using **interpolation** the particle stiffness that results in the measured bulk stiffness can be determined.

The contact stiffness highly affects the time step: the higher the stiffness, the smaller the time step. As a result many DEM simulations use a reduced stiffness:

> **Hint**:
>
> - For the ***Hertz-Mindlin*** contact model, realistic bulk flow results can often be achieved using relatively low values for Young’s modulus, starting at 1e7 Pa and calibration is not necessary and often not performed.
> - With the ***linear*** contact model, a lower-end contact stiffness would be in the order of 1e4 N/m.

### 5. Particle density calibration

It is done by filling a container with numerical particles and changing the particle density iteratively to achieve the desired bulk density. The relationship is linear and it only takes 3-4 iterations. The particle density highly influences the time step and flowability.

> **Note:** Make sure that the system reaches static equilibrium after each change in density.

### 6. Particle-particle friction coefficient Calibration

It cannot be directly measured. And among the other parameters particle-particle friction has to compensate the idealization made for particle size and shape for computational efficiency. Researchers have used many experiments such as **angle of repose**, **discharge test**, **draw down test** and **direct shear test**.

#### Using direct shear test

*The bulk friction* increases non-linearly with an increase in *particle-particle friction coefficient* and reaches an asymptotic value at higher friction coefficients. It can be obtained by using **interpolation**.

#### Using angle of response (AoR)

If direct shear test is weather not available or not applicable, the angle of repose test can be used alternatively.

This is almost a standard method for particle-particle **sliding** and **rolling friction coefficients** (rolling for spherical particles) calibration.

*The angle of repose* also increases non-linearly with an increase in friction coefficient, reaching an asymptotic value with higher friction coefficients. **Interpolate** for the coefficient of friction that results in an angle of repose within the range of the experimental value.

> **Note:** It is reported that for the same system the angle of repose reached an asymptotic value at lower friction coefficients in comparison to the direct shear test. Therefore it is recommended that for **materials with relatively high levels of friction -above 0.3-** to use **direct shear test** to calibrate the particle-particle coefficient.

> **Hint**: It is recommended that for non-spherical particles at least one and for spherical particles at least two experiment/measure to be used -*the more experiments are conducted the more accurate results are achieved*-.
>
> > - The drop down test as well as the direct shear test deliver four results. However, not all of the test results can be called independent. For instance, the two AoR results and the remaining mass in the upper or lower chamber of the drop down test are depending on each other. The higher the AoR in the upper chamber, the higher the remaining mass here. In the direct shear test the shear response at different normal stresses can be used, as well as the internal friction angle and the time to reach failure.
> > - The problem of superimposing different test results is that in all cases an intersection of the result isolines cannot be reached. considering the measurement error can reduce the possible parameter combinations. Optimization algorithms can also be used to reduce computational time.

### 7. Check bulk density

The bulk density can be influenced by the particle-particle friction coefficient and the rolling friction coefficient, therefore the calibration of the density should be revisited after these friction coefficients were calibrated (by iterating between steps 5 and 6).

## A fully-automated calibration workflow for DEM models of cohesive powders by [Orefice et al.](https://www.sciencedirect.com/science/article/pii/S0032591019310137)

This is a new automatized calibration method of DEM parameters to model particles ranging from very cohesive powders -exhibiting plastic compressibility of up tp 25%- to free-flowing particles. Since this study aimed to develop a calibration process for industrial-scale pharmaceutical processes where population of particles is >10e6, it focuses on systems of **single-component spherical** powders to reduce computational costs. Moreover, it is developed to use routine small-scale experiments in order to use only small amount of expensive materials available.

## Prerequisites

- ### Experimental devices:

  1. An angle of repose (AoR) tester

  2. ##### FT4 powder rheometer (to do compression and shear tests)

- DEM model using:

  - linear spring-dashpot contact model
  - rolling resistance model presented by [Luding](https://link.springer.com/article/10.1007%2Fs10035-008-0099-x)
  - interaction law: adhesive [elasto-plastic model](https://www.sciencedirect.com/science/article/pii/S0032591019310137) which takes into account the hysteretic attractive force upon collision

> **Note**: It should be noted that granular materials have an intrinsic hysteretic nature -so for instance, they might have different behavior after each compression cycle, the pressure should be measured subsequently-.

## Specifying the value of measured/estimated parameters:

- ### Particle **shape** is assumed to be perfectly spherical

- Particle **size** follows a uniform distribution of mean r and extrema r ± 10% (particle average size is chosen to be the highest possible to limit the simulation time, provided the particles to be small enough to prevent the system from exhibiting finite-size effects). This can be done by specific set of simulation prior to calibration.

- The **total number of particles** is determined by the average particle size and by cylindrical casing volume.

- Particle **density** is directly obtained from experimental measurement.

- **Maximum elastic spring stiffness** and **restitution coefficient (CoR)** are fixed a priori to limit the minimum collision time and, with it, the overall computation time.

- The **time step** chosen for the integration of the equations of motion satisfies the usual DEM requirement: dt ≤ tc/50 necessary for granting numerical stability.

- The **collision time** is obtained by solving the dynamics [equations of a damped harmonic oscillator](https://www.tandfonline.com/doi/abs/10.1080/19648189.2008.9693050) of spring stiffness.

- The **torsion friction coefficient** is set to zero.

- The **dimensionless plasticity depth** is calculated by a derived [equation](https://www.sciencedirect.com/science/article/pii/S0032591019310137).

> **Note**: in their study, the friction coefficient of wall was set to the particles' counterparts.

## Performing laboratory tests

- ### **Angle of repose (AoR)**

  Using this test, the powder heap height and the radius of the powder pile is measured. Consequently the angle of repose is computed. This test is repeated three times.

- **Uniaxial compression test**

  A set of 16 prescribed pressure data points are defined and the piston displacement is measured, producing pressure-deformation curves to depict how the bulk deformation is related to the applied pressure.

- **Shear cell test**

  In this test, at the same target pressures as in the uniaxial compression test, the piston torque measurement is carried out. The objective is to quantify the magnitude of resistive forces i.e. inter-particle friction and cohesion. Both sliding friction and cohesive stiffness can reproduce this curve and be calibrated.

## Numerical calibration workflow

### 1. Angle of response

##### Due to the jamming the funnel by the very cohesive powder, the AoR is numerically modeled by the **draw down test** and the discrepancies are prevented by re-calibrating the friction coefficient in the shear test. It should be noted that performing this step to calculate a primary value for the friction coefficients is crucial since it affects the compression test.

#### 1.1. Initialization:

While plastic stiffness has negligible effect on determining the angle of repose, cohesive stiffness should be initialized carefully since its value affects the calibrated sliding friction coefficient (here k_c is the dimensionless cohesive stiffness):

- for α ≤ 30° initially set k_c = 10e−3
- for 30° ≤ α ≤ 50° initially set k_c = 5*10e−3
- for α ≥ 50° initially set k_c = 10e-2

#### 1.2. AoR (Calibration of sliding and rolling friction coefficient and cohesion stiffness)

The angle of repose is monotonically dependent on **sliding coefficient of friction**.

- The first two steps are conducted by two first guess -resulting in a boundary which contains the target angle of repose- i.e. μ_s1 = 0.50 and μ_s2 = 0.05, and the new friction coefficient is then set to the average of the previous steps, resulting in a new angle of repose. The relative deviation between the numerically obtained angle of repose and the target experimental value is calculated and compared to a user defined tolerance. Via the bisection method described, the cycle is iterated until it is converged.
- If the first guess results in angle of repose of smaller than the target value, the **rolling friction coefficient** in increased by an amount of its initial value and the simulations are repeated.
- If the convergence did not meet, the rolling friction is increased until it either reaches its maximum allowed value or the angle of repose is met.
- Otherwise, the rolling friction is again set to its initial value, and **cohesion stiffness** is increased by an amount of its initial value and the simulations go on. Note that before each increase in cohesion stiffness, the rolling friction is progressively increased to until the first angle of repose is greater than the targeted value.

### 2. Powder rheometer

These simulations are lengthier since numerous data points must be met at once, hence the DEM parameters are tuned several times by an small amount of 0.001 times the actual calibrated variable each 5 timesteps.

In compression test, the **cohesion stiffness** is tuned to meet the pressure at each compression level.

During shear test, both **sliding friction** and **cohesion stiffness** are tuned to match the piston torque at each piston pressure.

Two criteria are exposed: ***mean relative deviation of calibrated variables*** and ***deviation of their mean from the starting value***. If the cycle does not converge, a new set of calibration cycle is performed with the new starting value equal to the mean of the calibrated values. The cycle is iterated until one of the following criteria are satisfied:

1. Both of the above mentioned deviations are less than a user-defined threshold.
2. The deviation of the mean of the calibrated variables are less than 0.001.
3. The number of iterations reaches a pre-defined maximum number.

#### 2.1 Uniaxial compression test (Calibration of plastic stiffness)

For each compression height, the pressure is computed by the summation over the all particles applying force (the vertical component) against the piston. The **plastic stiffness** is increased/decreased accordingly to finally reach the target pressure value.

#### 2.2 Shear test (Re-calibration of the sliding friction coefficient and cohesion stiffness)

The piston moves downwards to meet the prescribed pressure point and kept constant until the piston is then rotated at the experimental angular velocity and the torque along its axis, is calculated. Before tuning either of these two parameters, a particle rearrangement phase is performed, making sure that most of the particles are relocated by the piston motion.

Similar to the compression test, during each cycle multiple tuning of the variable is performed, but the sliding friction coefficient is calibrated *only* during compression and cohesion stiffness only during decompression.

> **Note**: since two parameters are calibrated at the same time, the range of the value sin each cycle should be restricted around the initial value e.g. 10%, to prevent divergence.