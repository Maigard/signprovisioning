# Sign Provisioning
This is a small start to building a dev environment for sign.

## Setup Instructions
1. Install Virtualbox - https://www.virtualbox.org/wiki/Downloads
1. Install Vagrant - https://www.vagrantup.com/downloads
1. Install Ansible - https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html 
    1. I usually install in a virtual environment to isolate it from the system.
    1. create the venv - `python -m venv /path/to/new/virtual/environment`
    1. activate the environment - `. /path/to/new/virtual/environment/bin/activate`
    1. install ansible with pip - `pip install ansible`
    1. install winrm with pip - `pip install "pywinrm>=0.3.0"
`. I ran into problems on Catalina and had to install six as well `pip install six`
1. start the systems - `vagrant up`
1. mount the web environment \\\\signWeb\surgery
