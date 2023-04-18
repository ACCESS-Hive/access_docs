# Getting Started with ACCESS-CM

This section outlines some key user requirements before getting started with running ACCESS-CM suites.

## Requirements for running ACCESS suites 

- An institutional email address with an organisation that allows access to NCI, e.g. CSIRO, a university, etc.
- Access to NCI compute/storage.
- A computer with an internet connection and a command line terminal with a Linux/Mac/Unix computer (e.g., MacOS with XQuartz and command line tools installed) or Putty Cygwin or similar X-Windows compatible program on a PC. 

### Basic Setup 
To run an ACCESS suite, all new users will need to:

- [Create an NCI account](https://opus.nci.org.au/display/Help/How+to+create+an+NCI+user+account) through the NCI online self-service portal.
- [Join the ACCESS group](https://my.nci.org.au/mancini/project/access/join). You can also find instructions on how to [join a particular project](https://opus.nci.org.au/display/Help/How+to+connect+to+a+project) through the NCI self-service portal. 
- [Connect to accessdev](https://accessdev.nci.org.au/trac/wiki/GettingConnected) once you have your NCI credentials and have been granted membership of the ACCESS group to complete your setup. At present, both accessdev and ARE environment run the models on Gadi. ARE, however, only supports shorter-running suites (i.e., runs less than 48 hours). Work is currently in progress to fully transition the cylc workflows from accessdev virtual machine to the ARE.
- Additional steps relating to [communication between accessdev and Gadi](https://accessdev.nci.org.au/trac/wiki/gadi) may also be necessary. 