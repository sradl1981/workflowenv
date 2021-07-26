Use Case 4 - Querying numerical data from  data base
======================

Sub-System:  LIGGGHTS (or Aspherix) - (distributed by DCS Computing GmbH) and Orange3

This use case describes how to query the available and archived simulation data from database, to be input into the calibration workflows defined in Orange3.


| Section                             | Comment                                                      |
| ----------------------------------- | ------------------------------------------------------------ |
| Use Case Name                       | Querying numerical data from  database                       |
| Scope                               | Querying specific numerical data from the successfully archived data available in the database |
| Level                               | Sub-Level data querying                                      |
| Primary Actor                       | Researchers who wants to calibrate a DEM model, or analyse data of DEM simulations |
| Stakeholders and Interests          | Researchers who perform DEM simulations or develop DEM models, experimentalists who conduct tests for calibration of DEM models |
| Preconditions                       | A database in which the simulation data has been archived in that successfully |
| Success Guarantee                   | Accessing and reading the queried data from database is completed without error. Data is accessible from a python widget in Orange3. |
| Main Success Scenario               | The the is retrieved successfully from the database.         |
| Extensions                          | -                                                            |
| Special Requirements                | none                                                         |
| Technology and Data Variations List | input/output/log files of LIGGGHTS (or Aspherix)             |
| Frequency of Occurrence             | upon request in each calibration step                        |
| Miscellaneous                       | -                                                            |