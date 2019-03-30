ansible-mysql
=============

A simple example of MySQL database automation using Ansible.

To get started, first update the inventory file for your own hosts.
You may leave the variables as they are to run the example or customize
them. The required variables are as follows:

  * mysql_root_pw: This needs to be the unencrypted password for the root
    user.
  * mysql_dbs: This should be a list of databases to create.
  * mysql_users: This is a list of dictionaries with the following keys.
    * name: Name of the user to create
    * host: Host the user may connect from
    * password: The user's unencrypted password
    * privs: A list of privileges to grant the user

Once the inventory is updated, the following playbooks exist to demonstrate
the automation capabilities of Ansible:

  * setup.yml - This playbook will install MySQL, perform basic MySQL
    hardening, and then create entities as defined in the inventory.
  * setup_cmd_only.yml - This playbook demonstrates how the same task would
    be completed without using modules specific to any database software
    while maintaining idempotency. This is useful when working with database
    applications that may not be directly supported by Ansible. It
    demonstrates the flexibility of Ansible to automate any system with an
    interface.
  * teardown.yml - This playbook will undo most of the changes made by one of
    the setup playbooks.

To run a playbook, use a command similar to the following:

```
ansible-playbook -i inventory.yml setup.yml
```

