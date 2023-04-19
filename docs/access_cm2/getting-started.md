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

## Preparationing to run an ACCESS-CM suite
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
| `nci_account -P [proj]`| Compute allocation for [proj]          |
| `nqstat -P [proj]`     | Jobs running/queued in [proj]                   |
| `lquota`               | Storage allocation and usage for all your projects|

 
