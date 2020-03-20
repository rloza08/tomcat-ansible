## Role info

> Ansible Role to Install Tomcat 9 on CentOS, Fedora, Debian and Ubuntu Linux.

## How to use this role

- Clone the Project:

```
$ git clone https://github.com/rloza08/tomcat-ansible.git
$ cd tomcat-ansible
```

- Update your inventory, e.g:

```
$ vim hosts
[tomcat-nodes]
192.168.10.10       # Remote user to act on
```

- Update variables in playbook file - Set Tomcat version, remote user and Tomcat UI access credentials

```
$ vim tomcat-setup.yml
---
- name: Tomcat deployment playbook
  hosts: tomcat-nodes
  become: yes
  become_method: sudo
  remote_user: root
  vars:
    tomcat_ver: 9.0.33
    ui_manager_user: manageruser
    ui_manager_pass: managerpassword
    ui_admin_username: adminuser
    ui_admin_pass: adminpassword
  roles:
    - tomcat
```

If you are using non root remote user, then set username and enable sudo:

```
become: yes
become_method: sudo
```

## Running Playbook

Once all values are updated, you can then run the playbook against your nodes.

Playbook executed as root user - with ssh key:

```
$ ansible-playbook -i hosts tomcat-setup.yml
```

Playbook executed as root user - with password:

```
$ ansible-playbook -i hosts tomcat-setup.yml --ask-pass
```

Playbook executed as sudo user - with password:

```
$ ansible-playbook -i hosts tomcat-setup.yml --ask-pass --ask-become-pass
```

Playbook executed as sudo user - with ssh key and sudo password:

```
$ ansible-playbook -i hosts tomcat-setup.yml --ask-become-pass
```

Playbook executed as sudo user - with ssh key and passwordless sudo:

```
$ ansible-playbook -i hosts tomcat-setup.yml --ask-become-pass

```
```
