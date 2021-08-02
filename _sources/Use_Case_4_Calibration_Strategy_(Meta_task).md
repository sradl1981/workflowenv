Deciding about the calibration strategy (Meta-task)  
======================

Sub-System: -

This use case describes how to decide on the required experiment(s)/template(s) that should be used for the specific application that the DEM-parameter calibration is performed. the calibration tests should consider the nature of the real process which should be simulated and therefore the calibration process should be selected accordingly. The target flow situation (e.g. quasi-static, slow, high dynamical bulk material flow), material characteristics (extent of deformability, plasticity, cohesiveness, ...), and the suitable contact model and its required parameters should be taken into account. Since multiple combination of parameters can produce the target bulk response in every experiment, it is highly recommended to use either more than one experiment or to aim for more than one target measured response. 


| Section                             | Comment                                                      |
| ----------------------------------- | ------------------------------------------------------------ |
| Use Case Name                       | Deciding on the calibration strategy                         |
| Scope                               | Choosing the right calibration workflow                      |
| Level                               | Top-Level calibration strategy                               |
| Primary Actor                       | Researchers who wants to calibrate a DEM model, or have previous experience and deep knowledge in particle technology and DEM simulations |
| Stakeholders and Interests          | Researchers who perform DEM simulations or develop DEM models, experimentalists who conduct tests for calibration of DEM models |
| Preconditions                       | Deep knowledge about the sensitivity of common experiments to the input DEM parameters, contact models in DEM simulations, |
| Success Guarantee                   | Accessing and committing data to the database is completed without error. Data is available in the database and the calibration workflows and optimum order of performing the experiments in calibration workflows. |
| Main Success Scenario               | The suitable workflow is selected and the prerequisites for preforming such workflow within the workflow environment is available. |
| Extensions                          | -                                                            |
| Special Requirements                | The experimental devices (data), relational data, and corresponding calibration templates should be available. |
| Technology and Data Variations List | -                                                            |
| Frequency of Occurrence             | Before performing any calibration case                       |
| Miscellaneous                       | -                                                            |