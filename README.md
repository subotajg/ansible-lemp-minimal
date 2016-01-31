# ansible-lemp-minimal
Vagrant box (Debian) with ansible provisioning for Parallels Desktop VM.

It's minimalistic set, based on geerlingguy.* playbooks.

Nginx config is hardcoded in ``provisioning/templates/config.conf``
Mysql dump - ``data/db_dev_dump.sql``

Cloning actual webapps is done in
``provisioning/hostscript.sh``


To install on local machine, you should have:

- Parallels;
- Vagrant;
- Vagrant plugin (vagrant plugin install vagrant-triggers)
- Git ( projects are clonning by shell)
- Composer (composer install is done by shell)
if so, just run:

``vagrant up`` 

and have some coffee, because it takes some time ;)
