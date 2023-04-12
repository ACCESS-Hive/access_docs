
# ACCESS Model Configurations

## ACCESS-CM2

ACCESS-CM2 comprises: 

- Atmosphere model (UM10.6): N96 resolution (1.875° x 1.25°, 85 levels). Physical model only – no carbon cycle.

- Land surface model (CABLE2.5) 

- Ocean model (MOM5): Tripolar grid, 1° resolution, 50 levels.

- Sea ice model (CICE5.1) 

    | COMPONENT     | MODEL         | VERSION               |
    | ------------- | ------------- | --------------------- |
    | Atmosphere    | UM            | 10.6                  |
    | Land Surface  | CABLE         | 2.5 (integrated in UM)|
    | Ocean         | MOM	        | 5                     |
    | Sea Ice       | CICE          | 5.1                   |
    | Coupler       | OASIS-MCT     | 3                     |


**Experiments**

ACCESS-CM2 suites for CMIP6 Scenarios are listed on the [CSIRO's CMIP6 archive](https://confluence.csiro.au/display/ACCESS/CMIP6+Archive+-+ACCESS-CM2). 

- Portable ACCESS-CM2 CMIP6 suites available to the ACCESS community include: 



   | EXPERIMENT                     | SUITE         |
   | ------------------------------ | ------------- |
   | Pre-industrial Control         | Br-565        |
   |                                |               |

-----------------------------

## ACCESS-ESM1.5
ACCESS-ESM1.5 comprises:

- Atmosphere model (UM7.3): N96 resolution (1.875° x 1.25°, 38 levels). 

- Land surface model (CABLE2.4): same horizontal resolution as atmosphere (1.875° x 1.25°).

- Ocean model (MOM5): 1° resolution, 50 levels.

    | COMPONENT     | MODEL         | VERSION               |
    | ------------- | ------------- | --------------------- |
    | Atmosphere    | UM            | 7.3                   |
    | Land Surface  | CABLE         | 2.4 (integrated in UM)|
    | Ocean         | MOM	        | 5                     |
    | Sea Ice       | CICE          | 4.1                   |
    | Coupler       | OASIS-MCT     | 3                     |


**Experiments**

- Standard ACCESS-ESM1.5 CMIP6 Scenarios include:


    | Experiment   | Control | Link                                         |
    | ------------ | --------| -------------------------------------------- |
    | PIcontrol    | Payu    | ​https://github.com/coecms/esm-pre-industrial |
    | Abrupt4xCO2  |         |                                              |
    | 1pctCO2      |         |                                              |
    | Historical   | Payu    | ​https://github.com/coecms/esm-historical     |
    | AMIP         |         |                               |


[Payu](https://payu.readthedocs.io/en/latest/) is a workflow management tool for running climate models in supercomputing environments. 


__PMIP4__		
