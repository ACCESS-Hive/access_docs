# Rose stem

## Overview
The UM, JULES and LFRic all use rose stem for testing and as part of the ticket approval process (e.g., [UM working practices](https://code.metoffice.gov.uk/trac/um/wiki/working_practices#HowshouldItestmychanges)). There are NCI build and test configurations in all these.

The UM and JULES compare results to "known good output" files on disk whereas LFRic uses checksums (currently in the repository).

UM files are in `/g/data/access/KGO/standard_jobs/ifort20` and JULES in `/g/data/access/jules/rose-stem-kgo`. These need to be updated for new model releases and also when code changes between releases change results. This is rare with JULES but common with UM. The UM has an update script to make updating files simply but JULES does not.

## UM
For a description of the structure of the UM rose stem suite see [UM rose stem intro](
https://code.metoffice.gov.uk/trac/um/wiki/RoseStem/Introduction).

The NCI configuration has two main groups, `nightly` and `weekly` (equivalent to `nci`), defined in `rose-stem/site/nci/groups.rc`.  These include a subset of the tests that the Met Office run, [UM rose stem standard jobs](https://code.metoffice.gov.uk/trac/um/wiki/StandardJobs).

THe NCI `developer` group is quite sparse, so our convention has been to run the full `nci` group as part of the ticket approval process.

### Updating KGOs
The NCI configuration follows the Met Office definitions for the KGO variables for each test, see [variables.rc](https://code.metoffice.gov.uk/trac/um/browser/main/trunk/rose-stem/site/meto/variables_xc40.rc)

For a new release see [new UM release](install-um-release.md#um).

For a change between releases these may be updated as part of the Met Office commit process. Some times we may be advised on potential changes in advance, but more commonly we just see that `rose-ana` tasks have failed. The useful message is actually in `job.out` rather than `job.err`.

The same `kgo_update.py` script used for new releases can be used to update the KGOs for the ticket.
```
python2 kgo_update.py -S um_trunk -U $USER --non-interactive
```
## JULES
For a new release see [new JULES release](install-um-release.md#jules).

## LFRic
Run by BOM from gitlab?
