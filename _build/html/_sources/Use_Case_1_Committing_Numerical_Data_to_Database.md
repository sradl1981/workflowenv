
Committing Numerical Data to Database (from a Simulation) 
======================

Sub-System: LIGGGHTS (distributed by DCS Computing GmbH)

This use case describes how to commit data (incl. the metadata, simulation's input and reference parameters, all the simulation output files -either heavy raw outputs or averaged outputs-, and the status/validity of the results) to a database to be later used in a workflow management tool, e.g., to calibrate DEM models.


| Section                             | Comment                                                      |
| ----------------------------------- | ------------------------------------------------------------ |
| Use Case Name                       | Committing numerical data to database                        |
| Scope                               | Loading information about data and metadata and transfer to a database |
| Level                               | Top-Level data submission                                    |
| Primary Actor                       | Researchers who wants to calibrate a DEM model, or analyse data of DEM simulations |
| Stakeholders and Interests          | Researchers who perform DEM simulations or develop DEM models, experimentalists who conduct tests for calibration of DEM models |
| Preconditions                       | All the required input files, log files and outputs of the DEM model are available (DEM simulations are finished) |
| Success Guarantee                   | Accessing and committing data to the database is completed without error. Data is available in the database |
| Main Success Scenario               | Meta data file is created successfully                       |
| Extensions                          | -                                                            |
| Special Requirements                | none                                                         |
| Technology and Data Variations List | Standard input/output/log files of LIGGGHTS                  |
| Frequency of Occurrence             | after every successful LIGGGHTS simulation run               |
| Miscellaneous                       | -                                                            |
