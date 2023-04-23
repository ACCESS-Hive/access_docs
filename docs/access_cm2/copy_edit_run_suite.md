<!-- ---
hide:
    - toc
--- -->
<!-- Lines above to hide table of content -->
# Copy, Edit, and Run an ACCESS-CM2 suite

<div style="text-align: justify">
ACCESS-CM2 is a set of sub-models (eg. UM, MOM, CICE, CABLE, OASIS) with a range of model parameters, input data, and computer related information, that need to be packaged together as a <i>suite</i> in order to run.
<br>
Each ACCESS-CM2 suite has an ID, in the format <code>u-[suite-name]</code>, with <code>[suite-name]</code> being a unique identifier (e.g. <code>u-br565</code> is the CMIP6 release preindustrial experiment suite).
<br>
Typically, an existing suite is copied and then edited as needed for a particular run.
<br>
</div>

## Copy ACCESS-CM2 suites with Rosie

<div style="text-align: justify">
<a href = "http://metomi.github.io/rose/doc/html/tutorial/rose/rosie.html" target="_blank">Rosie</a> is an <a href = "https://subversion.apache.org/" target="_blank">SVN</a> repository wrapper with a set of options to work with ACCESS-CM2 suites.
<br>
To copy an existing suite, on <i>accessdev</i>:
<!-- Change this to gadi/ARE when it will be completely possible to run CM2 fully on gadi-->
<ol>
    <li>
        Run <code>mosrs-auth</code> to authenticate using your MOSRS credentials (see 
        <a href="../access_cm2/getting-started/#met-office-science-repository-service-mosrs" target="_blank">Met Office Science Repository Service (MOSRS)</a> for troubleshooting):
        <br>
        <img src="../assets/mosrs-auth_command.gif" alt="mosrs-auth command">
    </li>
    <li>
        Run <code>rosie checkout [suite-ID]</code> to create a local copy of the <code>[suite-ID]</code> from the UKMO repository (used mostly for testing and examining existing suites):
        <br>
        <img src="../assets/rosie_checkout_command.gif" alt="rosie checkout command">
        <br>
        Alternatively, run <code>rosie copy [suite-ID]</code> to create a new full copy (local and remote in the UKMO repository) rather than just a local copy. When a new suite is created in this way, a new unique name is generated within the repository, and populated with some descriptive information about the suite along with all the initial configuration details:
        <br>
        <img src="../assets/rosie_copy_command.gif" alt="rosie copy command">
    </li>
</ol>
For additional <code>rosie</code> options, run <code>rosie help</code>.
<br><br>
The suites are created in the user's <i>accessdev</i> home directory, under <code>~/roses/[suite-ID]</code>.
<br>
The suite directory usually contains 2 subdirectories and 3 files:
<ul>
    <li><code>app</code> --> directory containing the configuration files for the various tasks within the suite.</li>
    <li><code>meta</code> --> directory containing the GUI metadata.</li>
    <li><code>rose-suite.conf</code> --> the main suite configuration file.</li>
    <li><code>rose-suite.info</code> --> suite information file.</li>
    <li><code>suite.rc</code> --> the Cylc control script file (Jinja2 language).</li>
    <img src="../assets/suite_content.gif" alt="suite content" />
</ul>
</div>
----------------------------------------------------------------------------------------

## Edit an ACCESS-CM2 suite configuration with Rose GUI

<div style="text-align: justify">
<a href = "http://metomi.github.io/rose/doc/html/index.html" target="_blank">Rose</a> is a configuration editor which can be used to view, edit, or run an ACCESS-CM2 suite.
<br>
To edit a suite configuration, on <i>accessdev</i>:
<!-- Change this to gadi/ARE when it will be completely possible to run CM2 fully on gadi-->
<ol>
    <li>
        Run <code>rose edit &</code> (the <code>&</code> is optional and keeps the terminal prompt active while runs the GUI as a separate process) from inside the relevant suite directory (e.g. <code>~/roses/u-[suite_ID]</code>) to open the Rose GUI and inspect the suite information.
        <br>
        <img src="../assets/rose_gui.gif" alt="Rose GUI" style="width:700px"/>
    </li>
    <li>
        There are many settings that can be changed in a Rose GUI. However, there are a few that we definitely want to check and edit before we run a suite:
        <ul>
            <li>
                NCI Project
                <br>
                To make sure we run the suite under the NCI project we belong to, we can navigate to <i>suite conf --> Machine and Runtime Options</i>, edit the <i>Compute project</i> field, and click the <i>Save</i> button <img src="../assets/save_button.png" alt="Save button" style="height:1em"/>. (Check <a href="https://opus.nci.org.au/display/Help/How+to+connect+to+a+project" target="_blank">how to connect to a project</a> if you have not joined one yet).
                <br>
                If, for example, we belong to the <i>tm70</i> Project (ACCESS-NRI), we will insert <code>tm70</code> in the <i>Compute project</i> field:
                <br>
                <img src="../assets/rose_change_project.gif" alt="Rose change Project" style="width:700px"/>
            </li>
            <li>
                Total Run length / Cycling frequency
                <br>
                ACCESS-CM2 suites are often run in multiple steps, each of them constituting a cycle, with the job scheduler resubmitting the suite every chosen <i>Cycling frequency</i>, until the <i>Total Run length</i> is met.
                <br>
                To modify these parameters, we can navigate to <i>suite conf --> Run Initialisation and Cycling</i>, edit the respective fields, and click the <i>Save</i> button <img src="../assets/save_button.png" alt="Save button" style="height:1em"/>. The values are in the <a href="https://en.wikipedia.org/wiki/ISO_8601#Durations" target="_blank">ISO 8601 Duration</a> format.
                <br>
                If, for example, we want to run the suite for a total of 50 Years, and resubmit every year, we will change <i>Total Run length</i> to <code>P50Y</code> and <i>Cycling frequency</i> to <code>P1Y</code>. Note that the current maximum <i>Cycling frequency</i> is 2 years:
                <br>
                <img src="../assets/rose_change_run_length.gif" alt="Rose change run length" style="width:700px"/>
            </li>
            <li>
                Wallclock time
                <br>
                The <i>Wallclock time</i> is the time requested by the <a href="../getting-started/#pbs-jobs" target="_blank">PBS job</a> to run a single cycle. If this time is not enough for the suite to end its cycle, our job will be terminated before the suite can complete the run. 
                <br>
                If we change the <i>Cycling frequency</i>, we might need to change the <i>Wallclock time</i> accordingly. 
                <br>
                The time needed for the suite to run a full cycle depends on several factors, but a good estimation can be 4 hours per simulated year.
                <br>
                To modify the <i>Wallclock time</i>, we can navigate to <i>suite conf --> Run Initialisation and Cycling</i>, edit the respective field, and click the <i>Save</i> button <img src="../assets/save_button.png" alt="Save button" style="height:1em"/>. The value is in the <a href="https://en.wikipedia.org/wiki/ISO_8601#Durations" target="_blank">ISO 8601 Duration</a> format.
            </li>
        </ul>
    </li>
</ol>
For more details on how to edit other suite parameters using Rose GUI, such as component configurations, output variables (STASH), or science settings, check <a href="../rose_gui_user_guide" target="_blank">Rose GUI user guide</a>.
</div>
----------------------------------------------------------------------------------------

## Run an ACCESS-CM2 suite

<div style="text-align: justify">
After completing all the modifications to the suite, we are ready to run it.
<br>
ACCESS-CM2 suites run on <a href="../getting-started#gadi" target="_blank">Gadi(TO DO check link)</a> through a PBS job submission.
<br>
When the suite gets run, the suite configuration files are copied on Gadi under <code>/scratch/[Project]/$USER/cylc-run/[suite-ID]</code>, and a symbolic link to this folder is also created in the <code>$USER</code>'s home directory under <code>~/cylc-run/[suite-ID]</code>.
<br>
An ACCESS-CM2 suite is constituted by several tasks (such as checking out code repositories, compiling and building the different model components, running the model, etc.). The workflow of these tasks is controlled by Cylc.
<br>
<a href="https://cylc.github.io/cylc-doc/7.8.8/html/index.html" targe="_blank">Cylc</a> (pronounced ‘silk’), is a workflow manager that automatically executes tasks according to the model main cycle script <code>suite.rc</code>. Cylc deals with how the job will be run and the time steps of each sub-model, as well as monitoring all the tasks and reporting any error that might occur.
<br>
To run an ACCESS-CM2 suite, on <i>accessdev</i>:
<ol>
    <li>
        Run <code>rose suite-run</code> from inside the relevant suite directory (e.g. <code>~/roses/u-[suite_ID]</code>) to run the initial tasks.
    </li>
    <li>
        After these few small tasks get executed, the Cylc GUI will open up and you will be able to see and control all the different tasks in the suite as they are run.
    </li>
    <img src="../assets/cylc_GUI.gif" alt="TO DO Cylc GUI" />
</ol>
You are done! If you don't get any errors, you will be able to check the suite output files after the run is complete.
<br>
Note that, at this stage, it is possible to close the Cylc GUI. If you want to open it again, just run:
<code>gcylc ..... TO DO check command</code>.

</div>
----------------------------------------------------------------------------------------

## Check for errors and basic debugging

<div style="text-align: justify">
It is quite common, especially during the first few runs, to experience errors and job failures.
<br>
TO DO
</div>

----------------------------------------------------------------------------------------

## Suite output files
<div style="text-align: justify">
TO DO
</div>

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