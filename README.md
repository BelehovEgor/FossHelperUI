# SourceExplorer
Last updated by | Egor Belekhov | Nov 23, 2021 at 11:23 AM GMT+3
***

## Overview

We need an application that will reduce the time and simplify the work with git. It should provide the ability to manage all the necessary repositories from one place (change, update branches) as well as build and run the necessary parts of the project.


### Use Cases

SourceExplorer should be user to update, build and run microservices. The list of paths to the necessary repositories will be in the configuration file.
For each of them, it will be possible to see the included branch and change it to another existing branch.  The selected branch can be updated by performing a pull operation. 
The next option is to select a mod and build the project according to it.
And lastly launching the project. Also these possibilities should be available for a group of projects, i.e. the selection of settings and then the execution of the necessary logic for all of them.

### Implementation

This will be a desktop application developed using WPF. The configuration file mentioned earlier will be local in the first iteration, in the future it is planned to load it from a remote repository. 
It is planned to use the git application to work with repositories because the pool of scheduled tasks does not require complex commands (now checkout, pull, stash). 
All information will be presented in a table. One line in it corresponds to one project.  To select the necessary settings, whether branch selection or build mods, there will be a ComboBox with an available selection. In the case of branch selection, a local branch change will also be made. For each operation, buttons are provided to perform it. For joint operations will be used CheckBoxes, after selecting them it will be possible to perform operations (using button in header of table) simultaneously for several projects.

### Information security

Authorization in the version control system will be implemented via open auth.

### Validation

