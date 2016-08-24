## Provisioning

This project runs the playbook **provision.yml** which executes each of the following roles:

## Roles

### users

Manages ssh users for all the individuals on our team. Their public keys are in this repo.

### common

Updates apt caches and installs a bunch of common dependencies

### firewall-csf

Installs Fail2Ban to protect the server against basic brute force attacks and enhance security

### acl

Adds the ACL (Access Control List) module to enable granular permissioning on files and enhance security

### docker

Installs Docker to enable the server to run containers. Example application stacks we might want to install are Discourse and ELK and in future, Lackey after we Dockerize the application, allowing us to simplify this project & open up the avenues by which people can host Lackey

### nginx

General purpose web server configured to sit in front of Express

### nodejs

Node.js server side Javascript runtime required to run Lackey applications

### postgresql

Default Lackey database

### ntp

Network Time Protocol management

***

N.B Great respect and thanks go to the following for various playbooks on Ansible Galaxy:

- [ANXS/postgresql/](https://galaxy.ansible.com/ANXS/postgresql/)

We would be *delighted* if anyone in the community would send us a pull request reconfiguring this repo to use Ansible Galaxy instead of the current solution of committing them to this repo.