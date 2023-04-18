# How to Modify Ancillary files

## Creating ancillary files from netcdf
*Needs updating!*


## Ancillary file modification
### How to edit land sea masks
mask_edit.py is a GUI editor for land-sea masks, allowing flipping selected points from land to sea or vice-versa. Creates a list of changes that can be used by the CAP.

For more details see [AncillaryFileModification](https://accessdev.nci.org.au/trac/wiki/access/AncillaryFileModification).

### Getting the number of land points from a mask file

### Extract a sub-region from an ancillary file

### Extract or remove selected fields from a PP file

### Change an ancillary file calendar

### Change the stash code of a selected field

### Dump header and field information

### Change date in a dump file

### Interpolate ancillary file to a different grid

### Merge files

### Merge a subregion

### Alter values of a particular field

## How to convert to netCDF
### Climate model output
### UM timeseries output
### Variable grid model

## Modules
__um_fileheaders.py__
Field names of all the headers in a UM file. From ​https://access-svn.nci.org.au/trac/um/browser/trunk/src/utility/qxreconf/rcf_headaddress_mod.F90. Subtracted 1 from all values so they work with python arrays.

__umfile.py__
Defines a class with routines for reading and writing UM files. Used by almost everything else. Works with big and little endian, 32 and 64 bit files.

__stashvar.py__
Dictionary with UM STASH variable names indexed by section and item numbers (taken from STASHmaster file). Where available CF standard names and CMIP5 short names are also included.

__levelheights.py__
Calculate true heights of model levels above sea-level, depending on orography

__eqtoll.py__
Rotated grid calculations