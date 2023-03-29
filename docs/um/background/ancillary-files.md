# Ancillary files
This serves as an index page for various information on ancillary files

Ancillary files are the mechanism by which external data sources are entered into the Unified Model (UM). This includes model orography, soil and vegetation types, climatologies for sea surface temperature and sea ice.

## Purpose of ancillary files
[UMDP 70 Ancillary File Data Sources](​https://nf.nci.org.au/facilities/software/UM/7.8/umdoc_system/UM_docs/papers/pdf/p070.pdf)

[UMDP 73 Ancillary File Creation](​https://nf.nci.org.au/facilities/software/UM/7.8/umdoc_system/UM_docs/papers/pdf/p073.pdf)

## Ancillary files at NCI
Rose stem suites expect ancillary files to be in ...

## Ancillary generation code
Code repository, trac, documentation, e.g [ANCIL](​https://code.metoffice.gov.uk/trac/ancil)

## Suites for ancillary files

## ACCESS grid namelists

## Various issues
### Orography source data problems
### Mask issues

## Various python utilities

## Examples
*The following info needs updating!*
There are ancillary files at a number of standard resolutions in the directories `vayu:/data/projects/access/ancil and cherax:~access/umdir/vn6.3/ancil/atmos`.

Some of these also have a version with a `_360 suffix` to denote use of a 360 day calendar which is used by the climate model. Note that all the ancillary files contain information about the calendar in their header and the model will complain if the wrong one is used. E.g. there are different mask files in n96 and n96_360 (even though they differ by only a single byte in the header the model won't run if the wrong one is used).

Note that we can not reproduce these files exactly because they were generated with the `US Navy 10'` orographic dataset which has now been deprecated in favour of the GLOBE orography.

There is also an `n96_hadgem1` subdirectory. This has a different land mask to the standard N96 case (generated outside the normal ancillary file framework according to Clive).

### High resolution data sets

### Grid namelists

### Generating ancillary files

__1. Land Sea Mask__

__2. Orography__

__3. Vegetation and Soil__

__4. Soil moisture__

__5. Vegetation Fractions__

__6. Ozone__

### Resource requirements on solar
On solar, generating an N96 mask takes about 240 sec and needs a memory limit of about 1 GB.
