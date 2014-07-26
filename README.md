# weblabdeusto-playbooks

Ansible playbooks to install and manage WebLab-Deusto.


## Usage examples

### Using vagrant

    cd vagrant
    vagrant up 

### Using only ansible

    ansible-playbook --private-key=~/.vagrant.d/insecure_private_key --user=vagrant --inventory-file=dummy -vvvv --limit='local' main.yml --tags "folder"
