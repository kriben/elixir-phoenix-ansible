Phoenix framework for Elixir development box
============================================

Vagrant
-------
[Vagrant](http://www.vagrantup.com/) and
[Ansible](http://www.ansibleworks.com/) is used to setup the local development
environment.

The installation of following software will be described under:

* [VirtualBox](http://virtualbox.org/)
* [Vagrant](http://www.vagrantup.com/)
* [Ansible](http://www.ansibleworks.com/)

Instructions for Ubuntu
-----------------------

1. Install VirtualBox:

    `apt-get install -y virtualbox`

    Use the VirtualBox installer from http://virtualbox.org/ if the version in
    apt is older than 4.x (verify with
    `apt-cache show virtualbox | grep 'Version:'`).

2. Install the Vagrant package for Ubuntu from the
[Vagrant download page](http://www.vagrantup.com/downloads.html).

    The Vagrant version available in apt is (usually) outdated.

3. Install Ansible using pip:

    `pip install ansible`

    The Ansible version available in apt is (usually) outdated.

4. Install NFS package (required for folder sharing between host and guest):

    `apt-get install -y nfs-kernel-server`

5. OPTIONAL: Install the vagrant plugin which upgrades the vb guest addons when necessary
   `vagrant plugin install vagrant-vbguest`

6. Create the Vagrant dev VM:

    `vagrant up dev`

    This will download the base Vagrant box, configure a VM and provision it
    using Ansible. The provision step automatically installs erlang, elixir and the
    phoenix framework (plus all other needed packages). For more provisioning steps,
    please see `provisioning/`.

7. Login to the Vagrant VM by running:

    `vagrant ssh dev`

8. Start development:

    `mix phoenix.new hello_phoenix`
    `cd hello_phoenix`
    `mix phoenix.server`

    This will create and run the demo app.

    The demo is running on [http://localhost:4000](http://localhost:4000/)

9. OPTIONAL: Add a database user

    `sudo -u postgres createuser -P -s -e phoenix_user`

    Edit the database part of `config/config.exs` to match the user and password
    you just created. You should now be able to follow the database part of the phoenix
    tutorial.


Instructions for OSX
-----------------------
This part of manual will refer to the linux part when possible.

On osx it´s adviced to install homebrew. It will be used in the installation procedure.

1. Install homebrew
    Follow the instructions at [Homebrew´s site](http://brew.sh/).
    You will bea able to install various handy package with the `brew` command.

2. Install VirtualBox:

    Get the newest version from
    [Virtualbox download page](https://www.virtualbox.org/wiki/Downloads) and
    install it.

3. Install the Vagrant package for Ubuntu from the
    [Vagrant download page](http://www.vagrantup.com/downloads.html).

4. Install Ansible:

    Homebrew is well maintained and the packages are rapidly updated to the latest version. Install ansible
    with:
    `brew install ansible`

From this point on you can continue with the Ubuntu installation instructions,
starting at step 5.

Links
-----

* [Vagrant docs](http://docs.vagrantup.com/v2/)
* [Ansible docs](http://docs.ansible.com/)
