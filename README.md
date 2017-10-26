Authentication
==============

The purpose of this role is to set up authentication to the Active Directory Domain.

Requirements
------------

Ensure that an up to date version of both this role.

Role Variables
--------------

The default variables are stored in **defaults/main.yml** and are:

* packages_to_install:
* enabled_services:
* enabled_booleans:

Variables that should be set in either host or group vars are:

* ca_cert_location:
* bind_password
* bind_user

It is a good idea to use `ansible-vault encrypt_string` to encrypt the bind_user and bind_password variables.

The following variable is found in ansible-playbooks/vault/certs/$realm.yml and it should be encrypted.

* ca_cert:

Dependencies
------------

The pexpect package must be installed by pip.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - include: base.yml

    - hosts: all
      become: True
      become_method: sudo
      gather_facts: False

      vars_files:
        - vault/certs/{{ realm }}.yml

      roles:
        - authentication
        - authorization

License
-------

MIT

Author Information
------------------

The Development Range Engineering, Architecture, and Modernization (DREAM) Team.
