MusicPlayers
============

Ansible will install the files required by Digital Hifi to publish its own styling to Volumio

Requirements
------------

Volumio 2.x should be fully installed

Role Variables
--------------

common:
-------
- mail_to: should be a valid e-mail address, default to "noosterwijk@hotmail.com" 
- mail_from: should be a valid mail-account from your mail-server. Default to: "nico.oosterwijk@ziggo.nl"

juju4.adduser:
--------------
- adduser_user_name: username
- adduser_user_home: '/home/homedir'
- adduser_user_home_perms: '0700'
- adduser_user_comments: 'whatever you want in here'
- adduser_sudoroot: true of false
- adduser_password: 'this_should_be_changed'
- adduser_public_keys:
      - default.pub


Dependencies
------------

- adduser from juju4

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

