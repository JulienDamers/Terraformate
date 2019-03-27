# Terraformate
![Status](https://img.shields.io/badge/Status-In%20Development-red.svg)
![Distrib](https://img.shields.io/badge/Ubuntu-16.04-brightgreen.svg)
[![Version](https://img.shields.io/badge/Version-latest%20release-yellow.svg)](https://github.com/fcebron/Terraformate/releases/latest)

The aim of this project is to have a script capable of providing the first system upgrade and install a pre-defined [list of softwares](config/SoftwareList.md). This program was designed to be easily customisable. The features of this script are already provided in a lot of commercial or professional softwares like ansible... My aim was to do the same with a very easy syntax and a minimalist list of requirements, so that it can be used on embeded computers (e.g. raspberry pi, beaglebone...) to quickly deploy a config.

In the end, this script will also take a list of softwares you want to uninstall (usually pre-installed softwares are just a waste of space, so this will automate their uninstallation) and provide minor configurations for softwares installed (ie: deactivate root account for ssh connections,...).

See actual [CHANGELOG](CHANGELOG.md) for the list of implemented features.


## Installation

The wget and graphical installations requires no other software than the already packed with your system (if not please notify me with the issues).


### Wget installation
Download and extract the latest version (chose between the 2 following ways to do so):

- Zip file: ```wget https://github.com/fcebron/Terraformate/releases/tag/Terraformate_0.4.0.zip && unzip Terraformate_0.4.0.zip```
- Tar.gz file : ```wget https://github.com/fcebron/Terraformate/releases/tag/Terraformate_0.4.0.tar.gz && tar zxvf Terraformate_0.4.0.tar.gz```

Launch the script in super-user mode:

```cd Terraformate && chmod +x terraformate.sh```

```sudo ./terraformate.sh```


### Graphical installation
Download and extract the latest version:
- Click on the zip download in the main page of the repository.
- Then unzip the archive with your right-click tool and launch a terminal in the folder.
- Launch the script in super-user mode:

```cd Terraformate && chmod +x terraformate.sh```

```sudo ./terraformate.sh```


### Git installation
Install git:

```sudo apt update && sudo apt install git```

Clone this repository:

```git clone https://github.com/fcebron/Terraformate.git```

Launch the script in super-user mode:

```cd Terraformate && chmod +x terraformate.sh```

```sudo ./terraformate.sh```



## Help
Usage:

sudo ./terraformate.sh [-h] [-n] [-r] [-l file]

Arguments:

    -h      Help menu
    
    -n      No-reboot mode (the script will end without rebooting the computer). Warning! This argument is not compatible with the -r one.
    
    -r      Reboot mode (the script will cause the reboot of the computer). Warning! this argument is not compatible with the -n one.
    
    -l file Take file as the software list to install/uninstall. Default software list is: config/SoftwareList.md.


## Features

The script uses a pre-defined [list of softwares](config/SoftwareList.md) by default. I have put 2 lists of softwares in the config/ folder:
 - The default one [SoftwareList.md](config/SoftwareList.md): it corresponds to usual softwares that I use on my personnal computer.
 - The dev/work one [WorkList.md](config/WorkList.md).

The best way for you to use this scritp is to fork my repository (on Github), then clone it into your system, create a branch and modify or add a software list for your personnal usage!


### Script behavior
This script does the following things:
 - Generates a log folder and a log file.
 - Adds Canonical's partner repository to "/etc/apt/sources.list".
 - Checks if "aptitude" is present inside the system (required in the following steps).
 - Uninstalls softwares unticked in the software list (see files in the config/ folder and -l option).
 - Updates and upgrades the system.
 - Installs the softwares ticked in the software list (see files in the config/ folder and -l option).
 - Removes old dependencies with "apt autoremove".



## Disclaimer
This script isn't compatible with snaps, because I don't use it. Don't expect to see this feature in the upcoming versions!

This script has been tested on:
* KDE neon 5.12
