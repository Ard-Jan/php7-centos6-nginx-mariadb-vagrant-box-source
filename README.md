# php7 Centos6 Nginx MariaDB Vagrant Box

Source environment for my [php7 Centos6 Nginx MariaDB](https://app.vagrantup.com/ajnijland/boxes/php7-centos6-nginx-mariadb) vagrant box. Provisioned using Ansible.

### Pre-reqs

* [Ansible](http://docs.ansible.com/ansible/index.html)

### Versions
> Basebox:centos/6 >= 1803.01

* CentOS release 6.9 (Final)
* Git 2.x
* PHPUnit 6.1.0
* Nginx 1.14.0
* Composer - latest
* PHP 7.2.x
* MariaDB 10.2.14


### Instructions

* `vagrant up`
* Make any changes you need to the box. Be sure to reflect these changes in the provisioning scripts.
* Before packaging up the box, ssh in, and run the commands that are in the comments at the end of this readme.
* Package up the box with `vagrant package --output php7-centos6-nginx-mariadb-0.1.0.box`. Replace `0.1.0` with the version number.
* Destroy the vm with `vagrant destroy --force`.
* Add the new box to vagrant's local list with: `vagrant box add php7-centos6-nginx-mariadb-010 php7-centos6-nginx-mariadb-0.1.0.box`. Again, replace `010` and `0.1.0` with the version number.
* Delete the `.vagrant` folder with `rm -rf .vagrant`.
* Test out the box by going to a different folder, running `vagrant init php7-centos6-nginx-mariadb-010`, and changing the `Vagrantfile` to fit your needs. Next, run `vagrant up`, and ensure everything is working.
* Create a new version on Vagrant Cloud.
* Add a new provider to the version. The type should be `virtualbox`. Upload the `.box` file output by the `vagrant package` command above.

### Pre-packaging commands

* `sudo rm /etc/udev/rules.d/70-persistent-net.rules`
* `sudo yum clean all`
* `sudo rm -rf /tmp/*`
* `sudo rm -f /var/log/wtmp /var/log/btmp`
* `sudo dd if=/dev/zero of=/bigemptyfile bs=1M`
* `sudo rm -rf /bigemptyfile`
* `sudo su`
* `history -c && exit`
* `cat /dev/null > ~/.bash_history && history -c && exit`
