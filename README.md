Ansible Networking Demo
=========

These playbooks can be used to demo Ansible Networking on rhpds

Pre-Reqs
------------

* Order F5 and/or Cisco rhpds

* If ordering both we will use the F5 Tower node as the control node for everything (the Cisco control node can't talk to the F5).

* If showing both Cisco & F5 - Copy Cisco inventory from ~/networking-workshop/lab_inventory/hosts to somewhere on the F5 control node - somewhere like ~/cisco-hosts

* If showing both Cisco & F5 - Copy Cisco private ssh key - ~/.ssh/aws-private.pem - to the F5 control node - somewhere like ~/.ssh/cisco_rsa. Make sure to set perms to 600


Tower Setup
--------------

*Make sure you load a license file into the F5 Tower node*

Now setup the F5 Tower demo

git clone https://github.com/pharriso/ansible_network_demo.git

cd ansible_network_demo

ansible-playbook bigip_setup_tower.yml

If you want to run the cisco demo from the F5 Tower then you need to edit some vars in the cisco_setup_tower.yml playbook:

inventory_file: Wherever you put the cisco inventory on the f5 control node
cisco_ssh_key: Wherever you put the cisco ssh key on the f5 control node

Then run the playbook:

ansible-playbook cisco_setup_tower.yml

Demo order (suggestion)
----------------

CLI Stuff

* Show Cisco inventory
* Show Cisco facts playbook - cisco_facts.yml
* Run the same playbook with -vv to show all facts
* Show reporting - cisco_report.yml
* Run Cisco config - cisco_config.yml
* Run F5 facts - bigip_facts.yml

Tower

* Explain Tower components - projects, credentials etc
* Run Cisco config playbook again from Tower - Show audit history
* Run F5 configure 
* Run F5 member playbook - shows survey.
* Show Cisco Config workflow
