# Atlassian Bamboo on CentOS 6, in Vagrant, using Ansible

The enclosed [Ansible](http://ansibleworks.com) playbook will install 
[Atlassian's Bamboo](https://www.atlassian.com/en/software/bamboo) CI server - 
an alternative to [Jenkins](http://jenkins-ci.org).

This uses a [@core CentOS6 Vagrant Box](http://vntx-box.s3.amazonaws.com/centos6.box) to 
install Bamboo into a [Vagrant](http://vagrantup.com) instance. The playbook could easily 
be applied to any host, running anywhere.

You need to [Ansible](http://ansibleworks.com) installed on your host system before 
running this up.

Look at [playbook.yaml](http://github.com/phips/bamboovm/blob/master/playbook.yaml) to 
see what Ansible is doing to the base CentOS6 
[box](http://docs.vagrantup.com/v2/virtualbox/boxes.html).

In summary, it is installing a java JDK, mysql-server and the mysql-jdbc-connector RPMs, 
then downloading Bamboo, untarring it, and setting a homedir in its properties. 
The Bamboo service is not started, it would be trivial to add a service starter as per 
[Atlassian's instructions](https://confluence.atlassian.com/display/BAMBOO/Running+Bamboo+as+a+Linux+service). The playbook also creates a MySQL database for Bamboo, the default 
user and password of which can be found in the playbook vars section at the head of the 
file.

For this simple example I've also chosen not to sit Bamboo behind Apache, although again, 
Atlassian have 
[trivial instructions](https://confluence.atlassian.com/display/BAMBOO/Integrating+Bamboo+with+Apache+HTTP+server).

Bamboo listens, by default, on port 8085. This is set as a forward in the Vagrantfile.
