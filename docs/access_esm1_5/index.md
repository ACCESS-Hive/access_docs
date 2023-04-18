# ACCESS-ESM1.5

## ACCESS-ESM1.5 configuration:

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


## Experiments

ACCESS-ESM1.5 suites for standard CMIP6 scenarios include:

| Experiment   | Control | Link                                         |
| ------------ | --------| -------------------------------------------- |
| PIcontrol    | Payu    | ​https://github.com/coecms/esm-pre-industrial |
| Abrupt4xCO2  |         |                                              |
| 1pctCO2      |         |                                              |
| Historical   | Payu    | ​https://github.com/coecms/esm-historical     |
|AMIP         |         |                               |

 

[Payu](https://payu.readthedocs.io/en/latest/) is a workflow management tool for running climate models in supercomputing environments. 