# Developing a Workflow tool for calibration of DEM models

## Raw ideas

1.	Defining the workflow tool (or maybe choosing a workflow from multiple possibilities) for the application
2.	Committing experimental Data to Database
3.	Plotting and reviewing the experimental results
4.	Simulate the specific calibration experiment
5.	Determine the model parameters to be calibrated by each simulation test; prepare the input files (type-1: constant measured/calibrated input variables file and type-2: initialized/to-be-calibrated variables)
6.	Submitting simulations to a remote cluster to be run
7.	**Committing Numerical Data to Database**
8.	**Plotting and reviewing the numerical results**
9.	Comparing the numerical and experimental results
10.	Deciding to renew the calibrated variables and repeat the simulations with new inputs or to move the calibrated variables from type-2 to type-1
    This continues, until no type-2 input variable is remained.

> **Note:** The numbering does not show the exact sequence of the workflow process, but the component of a calibration workflow. Based on the application (and the contact model that is chosen for the simulation) for which some input parameters have to be calibrated, a unique calibration workflow should be defined. In the workflow it is possible that the results of multiple experimental tests are used for calibration of a certain model paramet