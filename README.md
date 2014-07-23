weblabdeusto-playbooks
======================

Ansible playbooks to install and manage WebLab-Deusto.


Usage examples
--------------

Example using vagrant

    cd vagrant
    vagrant up 

Example directly using ansible:

    ansible-playbook --private-key=/home/tulvur/.vagrant.d/insecure_private_key --user=vagrant --inventory-file=dummy -vvvv --limit='local' main.yml --tags "folder"
