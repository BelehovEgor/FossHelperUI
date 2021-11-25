# GitRunner
Last updated by | Egor Belekhov | Nov 24, 2021 at 10:03 AM GMT+3
***

# GitRunner

## Overview

We need an application that will reduce the time and simplify the work with git. It should provide the ability to manage all the necessary repositories from one place (change, update branches).

### Use Cases

The tool should be able to:

1. When started, the application will pick up and display all git-repositories in the main git folder specified by the user. The user can select the main folder in Settings.
2. Synchronize repositories (all or selected). Pull the branch that is currently selected. Selected branch shall be visible to user.
3. Init feature: when requested, the application will download git repositories which are listed in the config file from the FossConnect DevOps.
If Initialization is requested again, the application will download repositories that are missing in the main git folder.
4. Have an autostash feature - be able to stash changes for current branch before pulling.
5. App configuration file should contain the list of repositories that should be downloaded during the initialization, paths to .csproj files to use for Build and paths to .exe files to use for Run.
The app configuration should be maintained in the dedicated DevOps repository (during the first implementation iteration it can be stored locally)
5. Automatically prune branches that do not have remote branches.
6. Have the ability to manually add repositories for synchronization from FossConnect project.
7. Have some short meaningfull output in the UI and detailed logs in a file. There should be a dedicated buttons: 'View logs' to open log folder for convinience, 'View config' to open folder with it.
8. Build selected projects.
9. Run selected projects.
10. Introduce profiles that will contain lists of repositories that should be checked for synchronization.
11. Have the ability to start the tool from the command line passing the profile name as a parameter.

### Implementation

This will be a desktop application developed using WPF targeting .NET 6. It is planned to use the libgit2shart nuget package to work with repositories because this library is time-tested and will allow you to perform all planned operations and expand their list in the future. List of commands that are planned to be used now are : branch, checkout, pull, stash.

All information will be presented in the table. One line in it corresponds to one project.
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/mainwindow.png)

To select the necessary branch there will be a ComboBox with an available selection. 
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/selection.png)
Also, there will be a ComboBox for build mode. <br />
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/buildmode.png) <br />
For each operation, buttons are provided to perform it. If action is required to be performed on multiple projects, user must click on corresponding CheckBoxes and then on an action button in header of the table.
Special buttons are located on the menu bar at the top of the window. <br />
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/settings.png)
Profiles will allow you to save selected branches and projects, i.e. it will allow you to quickly switch between selected settings. Profiles can be edited and new ones can be created. <br />
![Image alt](https://github.com/BelehovEgor/FossHelperUI/raw/design/Images/profiles.png)

### Information security

Authorization in the version control system will be implemented via open auth. The user will be logged into the git on the local device.

### Implementation iterations

Tasks of the first iteration:
1. Synchronize repositories (all or selected). Pull the branch that is currently selected. Selected branch shall be visible to user.
2. Have an autostash feature - be able to stash changes for current branch before pulling.
3. Create and use local configuration file.
4. Automatically prune branches that do not have remote branches.
5. Have some short meaningfull output in the UI and detailed logs in a file. There should be a dedicated 'View logs' button to open log folder for convinience.
6. Building projects.
7. Runing projects.

Tasks of the second iteration:
1. Have the ability to manually add repositories for synchronization from FossConnect project.
2. Implementing profiles
3. Have the ability to start the tool from the command line passing the profile name as a parameter.
4. Implement Initialization - downloading repositories from Azure DevOps
5. Create the Azure DevOps repository for the config file
