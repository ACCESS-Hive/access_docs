
# ACCESS Model Configurations

## ACCESS-CM2
### Components

| COMPONENT     | MODEL         | VERSION               |
| ------------- | ------------- | --------------------- |
| Atmosphere    | UM            | 10.6                  |
| Land Surface  | CABLE         | 2.5 (integrated in UM)|
| Ocean         | MOM	        | 5                     |
| Sea Ice       | CICE          | 5.1                   |
| Coupler       | OASIS-MCT     | 3                     |


ACCESS-CM2 comprises: 

- Atmosphere model (UM10.6): N96 resolution (1.875° x 1.25°, 85 levels). Physical model only – no carbon cycle.

- Land surface model (CABLE2.5) 

- Ocean model (MOM5): Tripolar grid, 1° resolution, 50 levels.

- Sea ice model (CICE5.1) 

-----------------------------

## ACCESS-ESM 1.5
### Components

| COMPONENT     | MODEL         | VERSION               |
| ------------- | ------------- | --------------------- |
| Atmosphere    | UM            | 7.3                   |
| Land Surface  | CABLE         | 2.4 (integrated in UM)|
| Ocean         | MOM	        | 5                     |
| Sea Ice       | CICE          | 4.1                   |
| Coupler       | OASIS-MCT     | 3                     |

ACCESS-ESM 1.5 comprises: 

- Atmosphere model (UM7.3): N96 resolution (1.875° x 1.25°, 38 levels). 

- Land surface model (CABLE2.4): same horizontal resolution as atmosphere (1.875° x 1.25°).

- Ocean model (MOM5): 1° resolution, 50 levels.


### Experiments
__Standard CMIP6 Scenarios__:

| Experiment    | Control       | Link                                         |
| ------------- | ------------- | -------------------------------------------- |
| PIcontrol     | PAYU          | ​https://github.com/coecms/esm-pre-industrial |
| Abrupt4xCO2   |               |                                              |
| 1pctCO2       |       	    |                                              |
| Historical    | PAYU          | ​https://github.com/coecms/esm-historical     |
| AMIP          |               |                                              |


__PMIP4__:		
