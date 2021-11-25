# GitRunner
Last updated by | Egor Belekhov | Nov 24, 2021 at 10:03 AM GMT+3
***

# GitRunner

## Overview

We need an application that will reduce the time and simplify the work with git. It should provide the ability to manage all the necessary repositories from one place (change, update branches).

### Use Cases

The tool should be able to:

1. Synchronize repositories (all or selected). Pull the branch that is currently selected. Selected branch shall be visible to user.
2. Have an autostash feature - be able to stash changes for current branch before pulling.
3. Have a yaml configuration file in a repo to get the configuration from. App configuration should contains paths to the local repositories.
4. Automatically prune branches that do not have remote branches.
5. Have the ability to manually add repositories for synchronization from FossConnect project.
6. Have some short meaningfull output in the UI and detailed logs in a file. There should be a dedicated buttons: 'View logs' to open log folder for convinience, 'View config' to open folder with it.
7. Build selected projects.
8. Run selected projects.
9. Introduce profiles that will contain list of repositories that should be checked for synchronization.
10. Have the ability to start the tool from the command line passing the profile name as a parameter.

### Implementation

This will be a desktop application developed using WPF targeting .NET 6. It is planned to use the libgit2shart nuget package to work with repositories because this library is time-tested and will allow you to perform all planned operations and expand their list in the future. List of commands that are planned to be used now are : branch, checkout, pull, stash.

All information will be presented in the table. One line in it corresponds to one project.
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/mainwindow.png)

To select the necessary branch there will be a ComboBox with an available selection. 
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/branchselecting.png)
Also, there will be a ComboBox for build mode. <br />
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/buildmodeselecting.png)  <br />
For each operation, buttons are provided to perform it. If action is required to be performed on multiple projects, user must click on corresponding CheckBoxes and then on an action button in header of the table.
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/projectchoice.png)
Special buttons are located on the menu bar at the top of the window. <br />
Profiles will allow you to save selected branches and projects, i.e. it will allow you to quickly switch between selected settings. Profiles can be edited and new ones can be created. <br />
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/editmenu.png)
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/viewmenu.png)
### Information security

Authorization in the version control system will be implemented via open auth. The user will be logged into the git on the local device.

### Implementation iterations

Tasks of the first iteration:
1. Synchronize repositories (all or selected). Pull the branch that is currently selected. Selected branch shall be visible to user.
2. Have an autostash feature - be able to stash changes for current branch before pulling.
3. Create and use local configuration file.
4. Automatically prune branches that do not have remote branches.
5. Have some short meaningfull output in the UI and detailed logs in a file. There should be a dedicated 'View logs' button to open log folder for convinience.

Tasks of the second iteration:
1. Have the ability to manually add repositories for synchronization from FossConnect project.
2. Implementing profiles
3. Building projects.
4. Runing projects.
5. Have the ability to start the tool from the command line passing the profile name as a parameter.