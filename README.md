# ansible-vagrant-centos-apache-mysql-php

Prepare for an vagrant, virtualbox, ansible.

## ssh config
### add `~/.ssh/config`

```
# vagrant
Host 192.168.33.*
IdentityFile ~/.vagrant.d/insecure_private_key
User vagrant
```

## vagrant settings
### set ip
`config.vm.network "private_network", ip: "192.168.33.xx"`

### set synced_folder
`config.vm.synced_folder "~/work/{project_name}", "/var/www/html",`

## vagrant ssh-config > ssh_config
### `vagrant up` after that type
`vagrant ssh-config > ssh_config`

## ansible connect check

```
$ls
README.md    ansible.cfg  playbook.yml ssh_config
Vagrantfile  hosts        roles
```

ok? after that type

```
$ ansible -i hosts front -a 'uname -r'
default | success | rc=0 >>
2.6.32-431.3.1.el6.x86_64
```

## go playbook

`ansible-playbook -i hosts playbook.yml`


## how to rsync auto

`vagrant rsync-auto`