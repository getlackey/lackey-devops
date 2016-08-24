# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

# Ansible version
ANSIBLE_DOWNLOAD_SOURCE = ENV['ANSIBLE_DOWNLOAD_SOURCE'] || "pip"
ANSIBLE_GIT_CHECKOUT = ENV['ANSIBLE_GIT_CHECKOUT'] || "HEAD"
ANSIBLE_GIT_REPOSITORY = ENV['ANSIBLE_GIT_REPOSITORY'] \
                          || "https://github.com/ansible/ansible.git"

# Managed boxes for this role
VMS = {
  :vagrant_trusty => {
    :box => "ubuntu/trusty64"
  }
}

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  VMS.each_pair do |name, options|

    config.vm.define name do |vm_config|

      # Set proper box
      vm_config.vm.box = options[:box]

      # Update system and install requirements
      vm_config.vm.provision "shell" do |sh|
        sh.inline = "test -f /usr/local/bin/ansible || (sudo apt-get update \
                            && sudo apt-get install build-essential libssl-dev libffi-dev \
                                                python-dev python-pip curl git language-pack-en -y \
                            && sudo pip install markupsafe cryptography paramiko PyYAML Jinja2 \
                                                httplib2 six ansible ansible-lint)"
      end

      # Use trigger plugin to set environment variable used by Ansible
      # Needed with 2.0 home path change
      vm_config.vm.provision "trigger" do |trigger|
        trigger.fire do
          ENV['ANSIBLE_ROLES_PATH'] = 'roles'
        end
      end

      # Run Ansible provisioning
      vm_config.vm.provision "ansible" do |ansible|
        ansible.playbook  = "playbooks/provision.yml"          
      end

    end
  end
end

