MusicPlayers
============

Ansible will install the files required by Digital Hifi to publish its own styling to Volumio

Requirements
------------

Volumio 2.x should be fully installed

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

- adduser from juju4
- motd from mrlesmithjr
- sudoers from salamachinas

Main Playbook
-------------

    - hosts: musicplayers
      roles:
        - common
        - { role: juju4.adduser, tags: 'adduser'}

License
-------

GPL

Author Information
------------------

Nico Oosterwijk < nico@digitalinfo.nl >

