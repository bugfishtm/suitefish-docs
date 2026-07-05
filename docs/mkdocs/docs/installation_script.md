# Installation via Script

## Introduction

!!! info "Information"
	Our script installation will always install suitefish in server-mode and occupy the whole server. You can find information about the different modes in the manual installation and requirement section.

In the github repository's `_scripts` folder, you'll find an installation script designed to install the full version with all features on a root server. This script is intended for users who wish to utilize our advanced hosting functionality on a fresh system. It is recommended only for advanced users with their own servers and infrastructure.

---------------

## Download the Script

You can download/view the script using the link below. This step is optional-only needed if you wish to review or upload the script manually, rather than following the standard installation instructions.

[Download](https://raw.githubusercontent.com/bugfishtm/suitefish-cms/refs/heads/main/_scripts/installer.sh){.md-button}

---------------

## Installation

This script is intended for use only on freshly installed servers and may corrupt running services or operations. In the github repository's `_scripts` folder, you'll find an installation script designed to install the full version with all features on a root/kvm server. This script is intended for users who wish to utilize our advanced hosting functionality on a fresh system. It is recommended only for advanced users with their own servers and infrastructure.

!!! danger "For your security, change the default password immediately after your first login."
	**Important:** To ensure the security of your account and system, it is strongly recommended to change the password right after your first login. Failing to do so may expose your system to potential security risks.

!!! info "Initial Username/Password for Suitefish"
	username: admin@admin.local  
	password: changeme  

Execute the following Commands and navigate through the installation shell process to install suitefish-cms on a fresh server with full root-level access.

```bash
curl -o ./installer.sh https://raw.githubusercontent.com/bugfishtm/suitefish-cms/refs/heads/main/_scripts/installer.sh
chmod u+x ./installer.sh  
sh ./installer.sh install
```
