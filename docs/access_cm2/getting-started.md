# Getting Started with ACCESS-CM
This section outlines some key user requirements and preparations before getting started with running ACCESS-CM suites.

To proceed further, you will need to have:

- An institutional email address with an organisation that allows access to NCI (e.g., CSIRO, a university, etc.).
- Access to NCI compute/storage.
- A Linux/Mac/Unix computer with an internet connection and a command line terminal (e.g., MacOS with XQuartz and command line tools installed, or Putty Cygwin/MobaXterm/similar X-Windows compatible program on a PC). 

## Requirements for running ACCESS-CM suites 

### Basic Setup 
To run an ACCESS-CM suite, new users will need to:

- [Create an NCI account](https://opus.nci.org.au/display/Help/How+to+create+an+NCI+user+account) through the NCI online self-service portal.
- [Join the ACCESS group](https://my.nci.org.au/mancini/project/access/join). You can also find instructions on how to [join a particular project](https://opus.nci.org.au/display/Help/How+to+connect+to+a+project) through the NCI self-service portal. 
- [Connect to accessdev](https://accessdev.nci.org.au/trac/wiki/GettingConnected) to complete your setup once you have your NCI credentials and are a member of the ACCESS group. 
*Note:* At present, both accessdev and [ARE](https://opus.nci.org.au/display/Help/ARE+User+Guide) run the models on Gadi. However, ARE only supports shorter-running suites (i.e., runs less than 48 hours). Work is currently in progress to fully transition the cylc workflows from accessdev virtual machine to the ARE.
- Additional steps relating to the [communication between accessdev and Gadi](https://accessdev.nci.org.au/trac/wiki/gadi) may also be necessary.

### UK Met Office Environment on NCI
As components within the ACCESS-CM suites use the UK Met Office model code, the [UK Met Office Environment](https://opus.nci.org.au/display/DAE/UK+Met+Office+Environment+on+NCI) is installed on NCI. This comprises the model software and tools as well as the cylc workflow system, rose suites, the Met Office MOSRS repository and our local replica repository. In order to checkout and run ACCESS-CM2 suites on Gadi using Rose/Cylc, you need to have access to a number of repositories at the Met Office as well as the local replica and local software on NCI, which will require fullfilling these [prerequisites](https://opus.nci.org.au/display/DAE/UK+Met+Office+environment+prerequisites).

### Met Office Science Repository Service (MOSRS)
[Met Office Science Repository Service (MOSRS)](https://code.metoffice.gov.uk) is a Trac server run by the UK Met Office for sharing code and configurations for the climate models it runs with partners. It contains the source code and configurations for the UM and JULES amongst other things.

To apply for a MOSRS account, you should contact your [local institutional sponsor](https://opus.nci.org.au/display/DAE/UK+Met+Office+environment+prerequisites).

--------------------------------------------

## Preparing to run an ACCESS-CM suite
At this stage, you should be able to connect to accessdev and Gadi. 

[accessdev](https://accessdev.nci.org.au) is a frontend system where you prepare ACCESS jobs and then submit them to [Gadi](https://nci.org.au/our-systems/hpc-systems) (the supercomputer at NCI where ACCESS is run).  

### Logging in to Gadi and accessdev
To run an ACCESS-CM2 suite (i.e., job), you need to first [login to Gadi](https://opus.nci.org.au/display/Help/0.+Welcome+to+Gadi#id-0.WelcometoGadi-LoggingIn&LoginNodes) with your `username` through a login node. 

`ssh -Y username@gadi.nci.org.au`

Similarly, to login to accessdev: 

`ssh -Y $USER@accessdev.nci.org.au`

The `–Y` switch is used to allow trusted X11 forwarding. Aliases and shortcuts can be created to simplify these commands by [configuring SSH](https://accessdev.nci.org.au/trac/wiki/Guides/SSH).


### Useful NCI commands 

| Command                |   Purpose                  |
| ---------------------- | -------------              |
| `logout` or `[ctrl-d]` | To exit a session          |
| `hostname`             | Displays login node details|
| `module list`          | Modules currently loaded   |
| `module avail`         | Available modules          |
| `nci_account -P [proj]`| Compute allocation for [proj]|
| `nqstat -P [proj]`     | Jobs running/queued in [proj]|
| `lquota`               | Storage allocation and usage for all your projects|

--------------------------------------------

## Gadi Resources
Coupled climate models like ACCESS-CM involve, among other things, calculation of complex mathematical equations that explain the physics of the atmosphere and oceans. Performed at hundreds of millions of points around the Earth, these calculations require vast computing power to complete them in a reasonable amount of time, thus relying on the power of  high-performance computing (HPC) like Gadi. The [Gadi supercomputer](https://nci.org.au/our-systems/hpc-systems) can handle more than 10 million billion (10 quadrillion) calculations per second and is connected to 100,000 Terabytes of high-performance research data storage.

An overview of [Gadi resources](https://opus.nci.org.au/display/Help/0.+Welcome+to+Gadi#id-0.WelcometoGadi-GadiResources) such as compute, storage and PBS jobs are described below. 

### Compute Hours
Compute allocations are granted to projects instead of directly to users and, hence, you need to be a member of a project in order to use its compute allocation. To run jobs on Gadi, you need to have sufficient allocated [compute hours](https://opus.nci.org.au/display/Help/0.+Welcome+to+Gadi#id-0.WelcometoGadi-ComputeHours) available, where the [job cost](https://opus.nci.org.au/display/Help/2.+Compute+Grant+and+Job+Debiting) depends on the resources reserved for the job and the amount of walltime it uses. 

### Storage 
Each user has a project-independent [`$HOME`](https://opus.nci.org.au/display/Help/0.+Welcome+to+Gadi#id-0.WelcometoGadi-TheHomeFolder$HOME) directory, which has a storage limit of 10 GiB. All data on `/home` is backed up.

Through project membership, the user gets access to the storage space within the
[project folders](https://opus.nci.org.au/display/Help/0.+Welcome+to+Gadi#id-0.WelcometoGadi-ProjectFolderonLustreFilesystems/scratchand/g/data) `/scratch` and  `/g/data` filesystems for that particular project.

### PBS Jobs
To run compute tasks such as an ACCESS-CM suite on Gadi, users need to submit them as *jobs* to *queues*. Within a [job submission](https://opus.nci.org.au/display/Help/0.+Welcome+to+Gadi#id-0.WelcometoGadi-JobSubmission), you can specify the queue, duration and computational resources needed for your job. When a job submission is accepted, it is assigned a jobID (shown in the return message) that can then be used to monitor the job’s [status](https://opus.nci.org.au/display/Help/0.+Welcome+to+Gadi#id-0.WelcometoGadi-QueueStatus). The [Gadi Quick Reference Guide](https://opus.nci.org.au/display/Help/Gadi+Quick+Reference+Guide) is an invaluable at hand resource.

On job completion, contents of the job’s standard output/error stream gets copied to a file in the working directory with the respective format: `<jobname>.o<jobid>` and `<jobname>.e<jobid>`. Users should check these two log files before proceeding with post-processing of any output from their corresponding job.

-----------------

## References 

<a id="1">[1]</a> 
Bodman, R. and Mackallah, C. and Dobrohotoff, P. (2020). 
Getting Started with ACCESS-CM2, 1-21.
https://nespclimate.com.au/wp-content/uploads/2020/10/Instruction-document-Getting_started_with_ACCESS.pdf

[@Bodman2020]
