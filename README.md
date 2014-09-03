# weblabdeusto-playbooks

Ansible playbooks to install and manage WebLab-Deusto.



## Requisites

The playbook depends on these other playbooks:

    ansible-galaxy install brad.virtualenv

## Usage examples

### Using vagrant

    cd vagrant/[subfolder]
    vagrant up
   
Please, check _vagrant/Vagrantfile_ for more information.

### Using only ansible

__Assumption__: you have a machine equivalent to the one created by vagrant in the previous step (see _vagrant/Vagrantfile_) in the IP defined by the _simple_ file.

    # Executing the whole playbook using the "simple" inventory with user "vagrant", etc.
    ansible-playbook -vvvv --user=vagrant --private-key=~/.vagrant.d/insecure_private_key --limit='local' ---inventory-file=simple main.yml
    
    # To execute only Weblab related steps
    ansible-playbook -vvvv -u vagrant --private-key=~/.vagrant.d/insecure_private_key -l 'local' -i simple main.yml --tags weblab

I will try to adhere to Ansible's [best practices](http://docs.ansible.com/playbooks_best_practices.html#content-organization) in the project organization. Therefore, [these usage patterns](http://docs.ansible.com/playbooks_best_practices.html#what-this-organization-enables-examples) should be applicable once the playbook is finished.


#### Installation in one machine

* Web server: Apache
* Persistence: MySQL
* Schedulling: Redis

    ansible-playbook -vvvv -u vagrant --private-key=~/.vagrant.d/insecure_private_key -l 'local' -i simple main.yml


#### Installation in three machines (one per role)

* Web server: Apache
* Persistence: MySQL
* Schedulling: Redis

    ansible-playbook -vvvv --private-key=/home/tulvur/.vagrant.d/insecure_private_key -u vagrant -l 'local' -i one_role_one_machine main.yml
    
Or if you prefer to do it step by step...

    ansible-playbook -vvvv --private-key=/home/tulvur/.vagrant.d/insecure_private_key -u vagrant -l 'local' -i one_role_one_machine dbservers.yml
    ansible-playbook -vvvv --private-key=/home/tulvur/.vagrant.d/insecure_private_key -u vagrant -l 'local' -i one_role_one_machine schedulingservers.yml
    ansible-playbook -vvvv --private-key=/home/tulvur/.vagrant.d/insecure_private_key -u vagrant -l 'local' -i one_role_one_machine webservers.yml
    

## Notes

If you are going to fork this and parametrize it with your own installation details, please make sure that either you don't version the resulting file or you use vault for the passwords.

For example, the file with the "global" variables (group_vars/local) stores a default database password.
