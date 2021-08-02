Use Case 5.3 - Commit Calibration Results to the DB
======================

Sub-System:  LIGGGHTS (or Aspherix) - (distributed by DCS Computing GmbH) 

This use case describes how to commit successful calibration results to the DB.


| Section                             | Comment                                                      |
| ----------------------------------- | ------------------------------------------------------------ |
| Use Case Name                       | Commit Calibration Results to the database                   |
| Scope                               | Loading the results and metadata about each calibration case to the database |
| Level                               | Low-level calibration data submission                        |
| Primary Actor                       | Researchers who wants to calibrate a DEM model, or analyse data of DEM simulations (A PhD student or Master student who has done DEM Simulations before) |
| Stakeholders and Interests          | Researchers who perform DEM simulations or develop DEM models, experimentalists who conduct tests for calibration of DEM models |
| Preconditions                       | The UC5.2 has successfully completed.                        |
| Success Guarantee                   | Accessing and committing the calibration results is completed without error and data is available in the database. |
| Main Success Scenario               | Metadata file is created successfully.                       |
| file Extensions                     |                                                              |
| Special Requirements                | -                                                            |
| Technology and Data Variations List |                                                              |
| Frequency of Occurrence             | upon request after each calibration workflow                 |
| Miscellaneous                       | -                                                            |