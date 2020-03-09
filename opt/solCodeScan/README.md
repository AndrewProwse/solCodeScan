# solSourceCode

### scs version 0.412

### Tue Nov 18 16:24:00 EST 2008


CountCat performs a quick and dirty analysis of lines of SPARC Solaris C-source code and tries to determine the effort required in porting to a Linux based system.  During the analysis of the source code, scs will flag any areas that may be of concern during the porting of the code.

## Supported OS:

Both Solaris and Linux are supported by this release of countcat.

## Installation:

To install scs, as root, untar the tarball in the / directory.

On first run of the scs script, it will ask you for the source system OS level, and also the OS of the target system.

## Running the scs Script:

Once the installation is complete, just run scs in the root of the source tree.

Example:


```bash
$ cd [source_code_dir]
$ /opt/scs/bin/scs [clean|reset|help]
```

During the execution of the script, scs will provide a quick summary on the console.  In addidtion, scs will leave an html formatted report, scs.html, and a more indepth, detailed report called scs.html.

This report, in addition to the Migration Guide, will help to identify occurances and level of difficulty of any possible issues on migrating code from SPARC Solaris to x86 Linux.

scs is to be used in conjuction with the Migration Guide.

## scs Command Line Options:

scs has three command line options:

### help

Help will display a description of the command line options.

### quick

scs just performs a quick file and line count of the c-source code and header files.

### clean

scs will restore itself back to it's initial `install fresh` condition before running.  This allows for selecting which release of Solaris the source code is coming from, and to which release of Linux the code is being ported to.

### reset 

Reset is the same as clean, but does not launch the scs script after cleaning.

## Script Flow:

The initial phase of scs inventories the source code tree and counts the number of file and the total num ber of lines of both C-source and header files.

Next, the header files are compared and sorted as follows:

1. Header files that are common between both Solaris and Linux
2. Header files that are in Solaris only
3. Header files that are included in the source code

Following this, pattern matching is performed looking for Solaris only system calls, library calls, socket calls, POSIX and Solaris threads ands semiphores.  Also, binary calls, union declarations, terminal i/o error messages and other such code is looked for.

Scripts are also searched, as they will have differences between the two platforms.

## Features/Bugs:

Currently scs does not distinguish comment lines from code.

