<!-- ---
hide:
    - toc
--- -->
<!-- Lines above to hide table of content -->
# <span style="color:orange">Rose, Cylc and Rosie</span>

<div style="text-align: justify">
ACCESS-CM2 is a set of sub-models (eg. UM, MOM, CICE, CABLE, OASIS) with a range of model parameters, input data, and computer related information, that need to be packaged together as a <i>suite</i> in order to run.
<br>
Each ACCESS-CM2 suite has an ID, in the format <code>u-[suite-name]</code>, with <code>[suite-name]</code> being a unique identifier (e.g. <code>u-br565</code> is the CMIP6 release preindustrial experiment suite).
<br>
Typically, an existing suite is copied and then edited as needed for a particular run. 
</div>

## Copying ACCESS-CM2 suites with Rosie

<div style="text-align: justify">
<a href = "http://metomi.github.io/rose/doc/html/tutorial/rose/rosie.html" target="_blank">Rosie</a> 
is an 
<a href = "https://subversion.apache.org/" target="_blank">SVN</a> 
repository wrapper with a set of options to work with ACCESS-CM2 suites.
<br>
To copy an existing suite, on <i>accessdev</i>:
<!-- Change this to gadi/ARE when it will be completely possible to run CM2 fully on gadi-->
<ol>
    <li>
    Run <code>mosrs-auth</code> to authenticate using your UK Met Office (UKMO) credentials (see <a href="">[TO DO add link to 'Getting started' section on MOSRS]</a> for troubleshooting):
    <br>
    (TO DO add gif of command)
    </li>
    <li>
    Run <code>rosie checkout [suite-ID]</code> to create a local copy of the <code>[suite-ID]</code> from the UKMO repository (used mostly for testing and examining existing suites):
    <br>
    (TO DO add gif of command)
    <br><br>
    Alternatively, run <code>rosie copy [suite-ID]</code> to create a new full copy (local and remote in the UKMO repository) rather than just a local copy. When a new suite is created in this way, a new unique name is generated within the repository, and populated with some descriptive information about the suite along with all the initial configuration details:
    <br>
    (TO DO add gif of command)
    </li>
</ol>
For additional <code>rosie</code> options, run <code>rosie help</code>.
<br><br>
The suites are created in the user's <i>accessdev</i> home directory, under <code>~/roses/[suite-ID]</code>.
<br>
The suite directory usually contains 2 subdirectories and 3 files:
<ul>
    <li>app --> directory containing the configuration files for the various tasks within the suite.</li>
    <li>meta --> directory containing the GUI metadata.</li>
    <li>rose-suite.conf --> the main suite configuration file.</li>
    <li>rose-suite.info --> suite information file.</li>
    <li>suite.rc --> the Cylc control script file (Jinja2 language).</li>
</ul>
(TO DO add gif of command)
</div>

<img src="/Users/davide/access-nri/access_docs/docs/access_cm2/assets/mosrs-auth_command.gif" alt="mosrs-auth command" />

## Copying ACCESS-CM2 suites with Rosie

<br><br><br><br><br><br><br>
Note that each suite directory is copied to Gadi
when it is run with cylc, where the scripts are then sent to the PBS job queue.
There are two ways of editing a suite, approaches that can be used individually or in
conjunction, whichever the user finds most useful or easier. One is to use the Rose
GUI, the other is to use a text/terminal editor (e.g. nano, nedit, etc.).


Note that each suite directory is copied to Gadi when it is run with cylc, where the scripts are then sent to the PBS job queue. There are two ways to edit a suite:

1. Use the Rose GUI
2. Use a text/terminal editor (e.g. nano, emacs, etc.).

Rose and cylc are invariably used together in rose/cylc suites.

## Rose 
[Rose](http://metomi.github.io/rose/doc/html/index.html) is a toolkit for writing, editing and running application configurations. Effectively a configuration editor, Rose starts a GUI to edit a rose suite, which is run from your suite directory on accessdev as follows: 

`cd ~/roses/u-[suite]`

`rose edit &` 

This creates a dialog box similar to the one shown below, where the `&` is optional (it keeps the terminal prompt active and runs the GUI as a separate process). 

![Rose_edit_gui](./rose-config-gui.jpg "Rose Edit GUI")

Alternatively, the following files can be edited directly using a text editor: 

`~/roses/u-[suite]/rose-suite.conf`

`~/roses/u-[suite]/rose-suite.info`

`~/roses/u-[suite]/suite.rc`


## Cylc 
Pronounced ‘silk’, [cylc](https://cylc.github.io/cylc-doc/7.8.8/html/index.html) is a workflow engine that automatically executes tasks according to schedules and dependencies. Effectively a job scheduler, cylc deals with specifications for how the job will be run and the time steps of each sub-model.

Cylc also provides important capabilities for monitoring jobs, particularly for dealing with jobs that have failed during processing but can be restarted from a previous timestep (rather than starting all over again).

At NCI, the current version cylc 7 will be soon replaced by cylc 8. 
 
<!-- References -->
<br>
<h6>References:</h6>
<ul style="font-size:0.8em;">
    <li>
        <a href = "https://confluence.csiro.au/display/ACCESS/Using+CM2+suites+in+Rose+and+Cylc" target="_blank">https://confluence.csiro.au/display/ACCESS/Using+CM2+suites+in+Rose+and+Cylc</a>
    </li>
    <li>
        <a href = "https://nespclimate.com.au/wp-content/uploads/2020/10/Instruction-document-Getting_started_with_ACCESS.pdf" target="_blank">https://nespclimate.com.au/wp-content/uploads/2020/10/Instruction-document-Getting_started_with_ACCESS.pdf</a>
    </li>
    <li>
        <a href = "https://code.metoffice.gov.uk/doc/um/latest/um-training/rose-gui.html" target="_blank">https://code.metoffice.gov.uk/doc/um/latest/um-training/rose-gui.html</a>
    </li>
</ul>