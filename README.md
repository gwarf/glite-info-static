# gLite Info Static

Documentation: http://gridinfo-documentation.readthedocs.io

## Authors

* David.Horat@cern.ch
* Laurence.Field@cern.ch

## Description

This application is an information provider that generates information in LDIF
format from combining an LDIF template with configuration values.

## Usage

Edit the corresponding .cfg file for your module and fill in the parameters
needed. Invoke glite-info-static without arguments for help if needed.
The resulting LDIF files will be created in the output/ directory.

## Core Structure

* glite-info-static: The main script to invoke
* README.md: This file

## Module Structure

  [name].1.cfg                  Config file to be filled out by the sysadmin
  [name]/
    [name].glue.ifc             Interface to comply with GLUE standard
    [name].wlcg.ifg             Interface to comply with WLCG standard
    [name].glue1.tpl            Template to create an LDIF for GLUE 1.3
    [name].glue2.tpl            Template to create an LDIF for GLUE 2.0


## TODO

None. :)

Do you have more suggestions?
Open an issue!

## Installing from source

```sh
make install
```

* Build dependencies: None
* Runtime dependencies: openldap

## Building packages

* It is possible to easily build pacakges CentOS using the provided
  `Makefile-build-docker` makefile leveraging the use of docker
  containers.

```sh
# Building a CentOS 7 RPM
make -f Makefile-build-docker rpm
```

## Changelog

* 0.1 (02/02/2010):
  * First draft
* 0.2 (03/02/2010):
  * Renamed the script from glite-info-static-create.sh to glite-info-create.sh
  * Help info embedded into the script (Laurence's request)
  * Use getops and parse more arguments (template name, cfg file path, etc.)
  * Improve script error handling and do more existence checks
* 0.3 (15/02/2010):
  * Fixed warning when a file didn't existed
  * Fixed problem: variable names in the middle of a line where not substituted
  * Able to use several .cfg files in one invocation
  * Now config files are at the script directory level, not inside the module
  * Directory renamed from glite-info-static-create to glite-info-create
  * Now the script changes to its directory wherever it is invoked from
  * Added more debug messages
* 0.4 (16/02/2010):
  * Now the default path for modules is hardcoded to: /etc/glite-info-create/
  * A new switch (-p) has been added to change the modules path
  * You can use several interfaces at once
* 0.5 (19/02/2010):
  * New option -o to change the output directory
  * Check for output directory existance, if it doesn't exist, create it
  * New option -v sets verbose mode: (0:ERROR, 1:WARNING, 2:INFO, 3:DEBUG)
  * Now all messages will be copied to syslog
  * Output successful messages: first the path, then list of files
