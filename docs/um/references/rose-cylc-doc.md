# Rosie, Rose and Cylc 
ACCESS-CM and ACCESS-ESM are a set of sub-models (e.g. UM, MOM, CICE, CABLE and OASIS) with a range of model parameters, input data, and computer related information, that need to be packaged together as a *suite* in order to run. Typically, an existing suite is copied and then edited as needed for a particular run. The suite resides in a directory created in the user’s accessdev `cylc-run` directory, e.g. `~/cylc-run/u-br565` (u-br565 is the ACCESS-CM2 preindustrial experiment release suite). 

Note that each suite directory is copied to Gadi when it is run with cylc, where the scripts are then sent to the PBS job queue. There are two ways to edit a suite:

1. Use the Rose GUI
2. Use a text/terminal editor (e.g. nano, emacs, etc.).

## Rose 
[Rose documentation](http://metomi.github.io/rose/doc/html/index.html)

## Cylc 
[Cylc documentation](https://cylc.github.io/cylc-doc/7.8.8/html/index.html)

At NCI, they are currently using cylc 7. Although cylc 8 has recently been released, it is awiting proper installation at NCI. 
 