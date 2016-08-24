## Getting Started

We assume you're developing on a Mac running OSX El Capitan.

### Requirements

- [VirtualBox](https://www.virtualbox.org/)
- [git](https://git-scm.com/) via XCode (Get from App Store)
- [rbenv](https://github.com/rbenv/rbenv) via [Homebrew](http://brew.sh) for Ruby
- [virtualenv](http://docs.python-guide.org/en/latest/dev/virtualenvs/) for Python
- [Vagrant](https://vagrantup.com/)

Make sure you have the XCode development tools installed:

    xcode-select --install
    
Put your organisations **secret** vault password as the sole content of a file here:

    ~/.vault_pass.txt

Setup the project with these commands in Mac Terminal:

    mkdir ~/dev
    cd ~/dev
    git clone git@github.com:getlackey/lackey_docker.git
    cd lackey_docker
    
Install a local Python environment to run Ansible from:

    virtualenv -p /usr/bin/python2.7 venv
    echo "# Add Ansible Vault Password" >> venv/bin/activate 
    echo "ANSIBLE_VAULT_PASSWORD_FILE=~/.vault_pass.txt" >> venv/bin/activate 
    source venv/bin/activate
    pip install ansible ansible-lint

N.B Remember that *you must source venv/bin/activate on each terminal session.*

Install a local Ruby environment for parity with Travis to run Ansible from:

    rbenv install 2.1.5
    rbenv local 2.1.5
    
Install any gems you need:

    gem install travis --no-rdoc --no-ri

N.B Not mandatory but this allows you to use the [.travis.yml command line linter](https://docs.travis-ci.com/user/travis-lint) via:

    travis lint .travis.yml    

Install this vagrant plugin:

    vagrant plugin install vagrant-triggers
    
You're good to go! Running this will create and provision a local VM and install all the things:

    vagrant up
    
    

    
