# Getting started

## Fast start

* Clone git repo
```sh
git clone git@github.com:express42/ansible-repertory.git
``` 
* Install [the latest release of Vagrant][Vagrant] if you will use exercise_05 with VMs

* Install prerequisites
```sh
cd exercise_05
touch vault.key
```
* Up VM
```sh
vagrant up
```
* Replace value at line ansible_ssh_private_key_file in file ./environments/example/inventory.yml with value from IdentityFile. You can found out it from:
```sh
vagrant ssh-config
```

* Run command
```sh
ansible-playbook site.yml --inventory-file=./environments/example/inventory.yml
```

* If you have "fail to connect to the host via ssh", you can try and repeat previous step:
```sh
ssh-keygen -f '/<your home directory>/.ssh/known_hosts' -R '192.168.56.4'
```
