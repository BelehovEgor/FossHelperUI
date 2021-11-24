# GitRunner
Last updated by | Egor Belekhov | Nov 24, 2021 at 10:03 AM GMT+3
***

# GitRunner

## Overview

We need an application that will reduce the time and simplify the work with git. It should provide the ability to manage all the necessary repositories from one place (change, update branches).

### Use Cases

The tool should be able to:

1. Synchronize repositories (all or selected). Pull the branch that is currently selected. Selected branch shall be visible to user.
2. Have the ability to change between schemas - change multiple repositories to 9.0 or 10.0 (master). Synchronization is considered a separate operation.
3. Have an autostash feature - be able to stash changes for current branch before pulling.
4. Have a yaml configuration file in a repo to get the configuration from.
5. Automatically prune branches that do not have remote branches.
6. Have the ability to manually add repositories for synchronization from FossConnect project.
7. Have some short meaningfull output in the UI and detailed logs in a file. There should be a dedicated 'View logs' button to open log folder for convinience.
8. Introduce profiles that will contain list of repositories that should be checked for synchronization.
9. Build application
10. Run application

### Implementation

This will be a desktop application developed using WPF targeting .NET 6. It is planned to use the Git CMD application to work with repositories because the pool of scheduled tasks does not require complex commands. List of commands that are planned to be used are : branch, checkout, pull, stash.

The configuration file mentioned earlier will be local in the first iteration, in the future it is planned to load it from a remote repository. 

All information will be presented in a table. One line in it corresponds to one project. 
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/fulltable.png)

To select the necessary branch there will be a ComboBox with an available selection. 
After branch selection, SourceExplorer will check if the branch is presented locally. 
If not - it will perform a pull operation.
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/branchselection.png)
Also, there will be a ComboBox for build mode. <br />
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/buildmode.png)  <br />
For each operation, buttons are provided to perform it. If action is required to be performed on multiple projects, user must click on corresponding CheckBoxes and then on an action button in header of the table.
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/choosing.PNG)

### Information security

Authorization in the version control system will be implemented via open auth. The user will be logged into the git on the local device.

### Implementation iterations

Tasks of the first iteration:
1. Synchronize repositories (all or selected). Pull the branch that is currently selected. Selected branch shall be visible to user.
2. Have the ability to change between schemas - change multiple repositories to 9.0 or 10.0 (master). Synchronization is considered a separate operation.
3. Have an autostash feature - be able to stash changes for current branch before pulling.
4. Create and use local configuration file.
5. Automatically prune branches that do not have remote branches.
6. Have the ability to manually add repositories for synchronization from FossConnect project.
7. Have some short meaningfull output in the UI and detailed logs in a file. There should be a dedicated 'View logs' button to open log folder for convinience.