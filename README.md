### About

N.B The Lackey Docker image is under development and not ready for production yet but check back soon. In the future this will be the recommended installation option as we evolve.

***

### Overview

[Lackey CMS](https://lackey.io) runs on specific versions of Node.js & PostgreSQL. Goal of this project is to provide a  configured example demo of the [Lackey Example Site](https://github.com/getlackey/lackey-cms-site) bundled up into a container.

- [Vagrant](https://vagrantup.com/) is an open source project to create and configure lightweight, reproducible, and portable development environments. We use it to easily bootstrap local Ubuntu VMs.

- [Docker](https://docker.com/) is an open source project to pack, ship and run any Linux application in a lighter weight, faster container than a traditional VM. We use it to *compartmentalise* our devops.

- This projects brief is it make it easier to deploy [Lackey CMS](https://github.com/getlackey/lackey-cms) and an [Example Lackey Site](https://github.com/getlackey/lackey-cms-site) on your servers, incl. demonstrating how to automate deployments, security & backup. 


### Getting Started

Follow this [getting started tutorial](/docs/getting-started.md) to set up your mac as a control machine & dev environment.

### Developing 

If you are looking to make modifications to this repository, you can easily test
out your changes before committing, using the magic of
[Vagrant](http://vagrantup.com).  Install Vagrant as per [the default
instructions](http://docs.vagrantup.com/v2/installation/index.html), and
then run:

    vagrant up

This will spawn a new Ubuntu VM, install Docker, and then await your
instructions. Once up, you may then SSH into the VM:

    vagrant ssh
    
Should you need, you may become `root` with `sudo -i`

If your VM is already running do this instead:

    vagrant provision


***

### License

MIT

### Inspiration:

- [Discourse](http://www.discourse.org/)
- [ansible-role-mysql](https://github.com/geerlingguy/ansible-role-mysql)

