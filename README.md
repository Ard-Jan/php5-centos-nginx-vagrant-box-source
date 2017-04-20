# php5-centos-nginx-vagrant-box-source

Source environment for my [php5-centos-nginx vagrant box](https://atlas.hashicorp.com/ajnijland/boxes/php5-centos-nginx/versions/0.1.0). Provisioned using Ansible.

### Pre-reqs

* [Ansible](http://docs.ansible.com/ansible/index.html)

### Versions
>Basebox:centos/6 1703.01
* CentOS release 6.9 (Final)
* Nginx 1.12
* PHP 5.6.30

### Instructions

* `vagrant up`
* Make any changes you need to the box. Be sure to reflect these changes in the provisioning scripts.
* Before packaging up the box, ssh in, and run the commands that are in the comments at the end of this readme.
* Package up the box with `vagrant package --output php5-centos-nginx-0.1.0.box`. Replace `0.1.0` with the version number.
* Destroy the vm with `vagrant destroy --force`.
* Add the new box to vagrant's local list with: `vagrant box add php5-centos-nginx-010 php5-centos-nginx-0.1.0.box`. Again, replace `010` and `0.1.0` with the version number.
* Delete the `.vagrant` folder with `rm -rf .vagrant`.
* Test out the box by going to a different folder, running `vagrant init php5-centos-nginx-010`, and changing the `Vagrantfile` to fit your needs. Next, run `vagrant up`, and ensure everything is working.
* Create a new version on Atlas.
* Add a new provider to the version. The type should be `virtualbox`. Upload the `.box` file output by the `vagrant package` command above.

### Pre-packaging commands

* `sudo yum clean all`
* `sudo dd if=/dev/zero of=/bigemptyfile bs=1M`
* `sudo rm -rf /bigemptyfile`
* `sudo su`
* `rm /etc/udev/rules.d/70-persistent-net.rules`
* `history -c && exit`
* `cat /dev/null > ~/.bash_history && history -c && exit`
