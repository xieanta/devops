# Getting started

## Fast start

* Install [the latest release of Vagrant][Vagrant] if you will use exercise_06 with VMs

* Use this command to generate ssh keys
```sh
ssh-keygen -t ED25519 -f ~/.ssh/vagrant
```
* Go to exercise-06 directory.
* Set up external role with command
```sh
ansible-galaxy install -r requirements.yml
```
* Up VM 
```sh
vagrant up
```

* If you have "fail to connect to the host via ssh", you can try and repeat previous step:
```sh
ssh-keygen -f '/<your home directory>/.ssh/known_hosts' -R '192.168.56.4'
```
