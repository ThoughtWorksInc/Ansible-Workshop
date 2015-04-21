Ansible
========

1. Vagrant
  - Vagrantfile is included in repo
  - In the Vagrantfile there are three OSes offered. Pick one.
  - Boot the selected machine

2. Ansible
  - Get vagrant ssh-config and place it in your ~/.ssh/config
  - Create an inventory file
  - Now run ```ansible default -m ping```
  - The ping module just check if Ansible works remotely
  - Now run ```ansible default -m setup```
  - The setup module shows you all the 'facts' available from that machine
  - The setup module will utilise facter and ohai if available
  - You can write custom fact collectors too
  - Now try ```ansible default -m copy -a 'src=example.yml dest=/tmp/test'```
  - This should copy the local file example.yml to the remote machine
  - Use vagrant ssh to check
  - This is Ansibles command line interface
  - Modules

3. Documentation
  - Ansible has documentation on their website
  - ansible-doc is like manpages for Ansible modules
  - Supports your own modules too

4. Playbooks
  - Vagrant provisioner is running example.yml file which right now does nothing
  - I've included a role that installs mysql
  - Add that to the list of roles in the example playbook
  - Run vagrant provision and you should have a running mysql server
  - Playbooks can have a task section but that isn't the preferred way to do things

5. Roles
  - Lets install Apache too...
  - Create a folder called apache in roles
  - Create a folder in the folder named tasks
  - Create a file in there called main.yml
  - The main.yml file of a role is automatically loaded and run
  - Lets support Debian, Ubuntu and CentOS
  - ansible_os_family stores the family of operating system
  - Add two includes, one for redhat, one for debain
  - Add a when clause on both these includes
  - You need to do two things in here
    - Set the name of the daemon in a fact (Debian is apache2 and RHEL is httpd)
    - Install the package using the right poackage manager
  - Now go back to main.yml and add a service module to start apache
  - Add a handler to restart apache if it is upgraded

6. Finally lets install and configure wordpress
  - Wordpress is at: ```http://wordpress.org/latest.tar.gz```
