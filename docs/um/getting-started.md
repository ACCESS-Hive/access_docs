# Getting Started with ACCESS suites

This section outlines some key user requirements before getting started with running ACCESS suites, tutorials, etc.

## Requirements for running ACCESS suites 

- An institutional email address with an organisation that allows access to NCI, e.g. CSIRO, a university, etc.
- Access to NCI compute/storage.
- A computer with an internet connection and a command line terminal (e.g. Unix or Linux computer, Terminal on MacOS with XQuartz and command line tools installed, Putty Cygwin or similar XWindows compatible program on a PC). 

### Setup 
To run an ACCESS suite, you will need to do the following:

- Setup an [NCI account](https://my.nci.org.au/mancini/signup/0) with a username and password, and then join a project. 
- Join the ACCESS group at https://my.nci.org.au/mancini/project/access/join 
- Once you have your NCI credentials and have been granted membership of the ACCESS group, follow [these instructions](https://accessdev.nci.org.au/trac/wiki/GettingConnected) to complete your setup. 
- Additional steps relating to [communication between accessdev and Gadi](https://accessdev.nci.org.au/trac/wiki/gadi) may be necessary. 


### MOSRS account
[Met Office Science Repository Service (MOSRS)](https://code.metoffice.gov.uk) is a Trac server run by the UK Met Office for sharing code and configurations for the climate models it runs with partners. It contains the source code and configurations for the Unified Model and JULES amongst other things.

To apply for a MOSRS account, users should contact their local institutional sponsor. These are:

- CSIRO: Martin Dix
- CLEX and Universities: Holger Wolff
- Bureau of Meteorology: David Lee

Members of CLEX can also email the helpdesk at cws_help@nci.org.au to request a MOSRS account.

*Note:* Additional steps are required to obtain access to the Met Office sharepoint and Yammer.

### UK Met Office Environment on NCI
Installation of the UK Met Office Environment on NCI comprises the cylc workflow system, rose suites, the Met Office MOSRS repository and our local replica repository as well the model software and tools.

Here is more information on how to setup your account to use the [UK MetOffice Environment on NCI](https://opus.nci.org.au/display/DAE/UK+Met+Office+Environment+on+NCI).
 

## Preparing to run ACCESS suites

### Logging in to NCI 
At this stage, you should be able to connect to accessdev and Gadi. 

[accessdev](https://accessdev.nci.org.au) is a frontend system where you prepare ACCESS jobs and then submit them to Gadi. 

[Gadi](https://nci.org.au/our-systems/hpc-systems) is the name of the supercomputer at NCI where ACCESS is run.  

To log into accessdev: 

`ssh -Y $USER@accessdev.nci.org.au`

The `–Y` switch is used to allow trusted X11 forwarding. 

You can now begin to work on setting up a model run, which is explained more in the *How-to Guides* and *Tutorials* sections. 

If required, enter UKMO password at the start of a session by typing `mosrs-auth`. It is needed for copying a suite and making any changes that affect the UM and its repository: 

To exit: `logout` or [ctrl-d] 

### Logging in to Gadi  
Logging into Gadi is similar to that for accessdev: 

`ssh -Y $USER@gadi.nci.org.au`

*Note:* Aliases and shortcuts can be created to simplify these commands by [configuring SSH](https://accessdev.nci.org.au/trac/wiki/Guides/SSH).

 Some useful NCI commands are: 
 
 `hostname` # displays login node details  

 `module list`  # modules currently loaded for you

 `module avail`  # available modules 

`nci_account -P [proj]` # compute allocation details for [proj]

`nqstat -P [proj]` # jobs that are running/queued in [proj]  

`lquota`  # storage allocation and usage for all your projects 

 To exit: the same as for accessdev. 