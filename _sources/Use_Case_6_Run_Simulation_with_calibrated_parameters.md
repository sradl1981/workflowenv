Run DEM simulations with calibrated parameters (validation)
======================

Sub-System:  LIGGGHTS (or Aspherix or any DEM software) 

This use case describes how to run a simulation with calibrated DEM parameters. It has to be noted that if this simulation is performed in order to validate the calibration procedure, the validation experiment should be sensitive to the calibrated parameters and should not be similar to the experiments that were used for the calibration.


| Section                             | Comment                                                      |
| ----------------------------------- | ------------------------------------------------------------ |
| Use Case Name                       | Run DEM simulations with calibrated parameters               |
| Scope                               | Performing DEM simulations (with any DEM software- Note: the implementation of the models used and the parameters should be similar to the one used in the calibration) |
| Level                               | High-level calibration                                       |
| Primary Actor                       | Researchers who wants to do a DEM simulations, or analyse data of DEM simulations (A PhD student or Master student who has done DEM Simulations before) |
| Stakeholders and Interests          | Researchers who perform DEM simulations or develop DEM models, experimentalists who conduct tests for calibration of DEM models, industrial engineer who wants to analyse a process |
| Preconditions                       | The UC5 (all the steps) has been successfully completed      |
| Success Guarantee                   | The simulation is run without any errors.                    |
| Main Success Scenario               | Prepare the input files for the DEM simulation (dependent on the software used). Start the DEM simulation. Check for any error or warnings. Fix the errors. The DEM software signals a successful simulation |
| file Extensions                     | -                                                            |
| Special Requirements                | none                                                         |
| Technology and Data Variations List | -                                                            |
| Frequency of Occurrence             | upon request for any calibrated sets of parameters available in database |
| Miscellaneous                       | -                                                            |

