# Ansible

* generate ssh key for user: ```ssh-keygen -t ed25519 -C "moshiur default"``` [enter passphrase]
* copy that ssh key to remote servers: ```ssh-copy-id -i ~/.ssh/id_d25519.pub {ip of the vm}```

* generate ssh key for ansible: ```ssh-keygen -t ed25519 -C "ansible"``` [no passphrase]
* copy that ansible ssh key to remote servers: ```ssh-copy-id -i ~/.ssh/ansible.pub {ip of the vm}```

* make a connection to all servers from source machine i.e. test is ansible is working fine or not: ```ansible all --key-file ~/.ssh/ansible -i inventory -m ping```
* create a ansible.cfg and run only : ```ansible all -m ping```

* list hosts: ```ansible all --list-hosts```
* gather everything about the remote servers: ```ansible all -m gather_facts```
* print only one server info: ```ansible all -m gather_facts --limit {ip}```

* run ansible with sudo permission: ```ansible all -m apt -a update_cache=true --become --ask-become-pass```
* install vim-nox to all hosts: ```ansible all -m apt -a name=vim-nox --become --ask-become-pass```
