## Fedora Workstation provisioning using Ansible

 Note: The playbook was tested only on Fedora 30.

### What the playbook does:

- Ensures the following are installed: 
    - git
    - vim
    - htop
    - exa
    - deluge

- Installs and enables **dash-to-dock** Gnome extension. It also adds some customizations like moving the dock to the bottom. (A restart may be needed for the changes to fully apply)
- Installs **docker and docker-compose**. It uses the latest supported version for fedora.
- Instals and configures **fish shell**. It includes **fzf** and **fzf fish plugin** to enable history search and the **pure** theme.
- Installs **Brave** browser
- Installs the following development tools:
    - Postman (https://www.getpostman.com)
    - Visual Studio Code (https://code.visualstudio.com/)
    - NodeJs (https://nodejs.org/en/)
    - Jetbrains toolbox is found in home folder
- Ensures a folder named **Projects** exists in the user's home directory
- Clones **devilbox** (LEMP/MEAN development environment) in the Projects folder. (https://github.com/cytopia/devilbox)
- Configures colors for git. It also adds name and email in .gitconfig if the corresponding variables are set in vars.yml
- Adds the following OS configuration :
     - Sets the hostname if the corresponding variable is set in vars.yml
     - Enables Automatic Login
- Adds the following keyboard shortcuts:
     - **Super+T** from Nautilus to open terminal from the current location in the file explorer
     - **CTRL+Shift+Esc** opens the Sytem Monitor
     - **CTRL+Alt+T** opens the terminal
     - **Super+D** hides all windows

Note: 
- Some dependencies needed to run the ansible commands might be installed as well, such as python3-psutil needed for the dconf command or unzip for installing dash-to-dock
- Running the playbook **will override** other custom keybindings

### Getting started
---

#### **1. Copy the vars.yml file**

```bash
$ cp vars.yml-example vars.yml
```
The vars.yml file contains some variables that can override the default variable in the Ansible roles

#### **2. Edit the vars.yml file**

By default all variables are commented out. To enable them, just uncomment and change the variables that you need.

---

#### **3. Run the provision.sh file**

What it does: 
1. Installs Ansible using dnf
2. Runs the Ansible playbook

```bash
$ ./provision.sh
```

Note: The script will ask for the sudo password twice: once for installing Ansible, and one more time for running the playbook.

