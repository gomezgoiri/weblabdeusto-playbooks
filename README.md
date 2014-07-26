# weblabdeusto-playbooks

Ansible playbooks to install and manage WebLab-Deusto.



## Requisites

    ansible-galaxy install brad.virtualenv

## Usage examples

### Using vagrant

    cd vagrant
    vagrant up
   
Please, check _vagrant/Vagrantfile_ for more information.

### Using only ansible

__Assumption__: you have a machine equivalent to the one created by vagrant in the previous step (see _vagrant/Vagrantfile_) in the IP defined by the _simple_ file.

    # Executing the whole playbook using the "simple" inventory with user "vagrant", etc.
    ansible-playbook -vvvv -u vagrant --private-key=~/.vagrant.d/insecure_private_key -i simple --limit='local' main.yml
    
    # To execute only Weblab related steps
    ansible-playbook -vvvv -u vagrant --private-key=~/.vagrant.d/insecure_private_key -i simple --limit='local' main.yml --tags weblab

I will try to adhere to Ansible's [best practices](http://docs.ansible.com/playbooks_best_practices.html#content-organization) in the project organization. Therefore, [these usage patterns](http://docs.ansible.com/playbooks_best_practices.html#what-this-organization-enables-examples) should be applicable once the playbook is finished.
