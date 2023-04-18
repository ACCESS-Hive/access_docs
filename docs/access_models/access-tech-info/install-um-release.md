# Installing a new Met Office release of the UM or JULES on gadi

## UM
Example here is installing `vn13.2`.

UM rose stem uses inputs from `~access/umdir/standard_jobs/inputs`. These are mirrored from JASMIN. However in practice they rarely change so copy the latest directory to the new version and then link back (this matches the structure on JASMIN). E.g.

```
cd ~access/umdir/standard_jobs/inputs
mv vn13.1 vn13.2
ln -s vn13.2 vn13.1
```

To build the new KGOs and create files for `~access/umdir/vnX.Y`, on `accessdev`
```
fcm co fcm:um.xm_tr um_trunk
cd um_trunk
rose stem --group=nci --group=install
```
All the `rose-ana` tasks will fail because of the missing KGOs. These have to be allowed to run so that the `kgo_update` script to be used next can get filenames.

Copy `admin/rose-stem/kgo_update/kgo_update.py` to `gadi` and then on `gadi`
```
python2 kgo_update.py -S um_trunk -U $USER --new-release --non-interactive
cp ~/cylc-run/um_trunk/work/1/atmos-gadi_intel_um_drhook_safe_omp-n48-1x2-noios-2t/drhook.prof.1 /g/data/access/KGO/standard_jobs/ifort20/gadi_intel_um_drhook_safe_n48/vn13.2/drhook.prof.1  # Not created by kgo_update
cp -r ~/cylc-run/um_trunk/share/vn13.2/ ~access/umdir
chgrp -R access.admin  ~access/umdir/vn13.2
```
Rerun the failed rose-ana tasks on `accessdev`. These should now all succeed.
```
cylc reset um_trunk -s waiting 'rose_ana*:failed'
```

To test the installation, upgrade the suite `u-aa124` to the latest version and run.
```
cd app/um
rose app-upgrade vn13.2
cd ../fcm_make
rose app-upgrade vn13.2
```
Update the GCOM module version in `suite.rc` and `VN` in `rose-suite.conf`.

### GCOM
GCOM is an MPI wrapper library used by the UM.
The GCOM library is built using `rose-stem`. This is set to build the library with both the Intel compiler ifort and with gfortran (the UM has been tested at NCI with gfortran but those tests aren't part of the trunk yet).

On `accessdev`,
```
fcm co fcm:gcom.xm_tr gcom_trunk
```
`rose stem/site/nci/suite.rc` has
```
{%- set MPI_VERSION = MPI_VERSION | default("openmpi/4.1.3") %}
```
The UM rose-stem tests are still using (as at vn13.2) `openmpi/4.0.2`, so this should be overridden on the command line
```
rose-stem --group=all -S MPI_VERSION=\'openmpi/4.0.2\'
```
This also works with `intel-mpi`.

When the rose stem tests are complete, create new modules for the MPI and serial versions of the library `~access/modules/gcom`. Naming convention is to append the openmpi version, e.g. for GCOM `vn8.0`
```
8.0_ompi.4.0.2
8.0_serial
```
Then in `~access/apps/gcom` (for example)
```
mkdir 8.0_ompi.4.0.2
cd 8.0_ompi.4.0.2
cp -r ~/cylc-run/gcom_trunk/share/nci_gadi_ifort_mpp/build/include .
cp -r ~/cylc-run/gcom_trunk/share/nci_gadi_ifort_mpp/build/lib .
chgrp -R access.admin ~access/apps/gcom/8.0_ompi.4.0.2
```
and similarly for the serial library.

Note that in the GCOM rose stem tests the `abort` tests are expected to fail and this is checked before the suite completes.

## JULES
To update the JULES rose-stem KGOs for a new release

Check out JULES trunk on `accessdev`
```
fcm co fcm:jules.xm_tr jules_trunk
cd jules_trunk
rose stem --group=all
```
All the comparison tasks will fail because the new KGO directory isn't there so use the cylc GUI to hold the `KGO_CHECK` group or from the command line
```
cylc hold jules_trunk 'nccmp*'
```
After all the tests have run, on `gadi` (assuming new release is `vn7.2`)
```
mkdir /g/data/access/jules/rose-stem-kgo/vn7.2
cp ~/cylc-run/jules_trunk/work/1/*/output/*.nc  /g/data/access/jules/rose-stem-kgo/vn7.2
chgrp -R access.admin /g/data/access/jules/rose-stem-kgo/vn7.2
```

Back on `accessdev`, release the comparison tasks which should now all succeed
```
cylc release jules_trunk 'nccmp*'
```
