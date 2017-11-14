MusicPlayers
============

Ansible will install the files required by Digital Hifi to publish its own styling to Volumio. It will also install additional services like ssmtp, cron and ntp.
cat

Requirements
------------

Volumio 2.x should be fully installed

Role Variables
--------------

common: (group_vars)
-------
- mail_to: should be a valid e-mail address, default to "noosterwijk@hotmail.com" 
- mail_from: should be a valid mail-account from your mail-server. Default to: "nico.oosterwijk@ziggo.nl"

volumio: (group_vars)
--------
- radiostation_uri: the URI for the webradio stream

Dependencies
------------

none

Main Playbook
-------------

    - hosts: musicplayers
      roles:
        - { role: common, tags: 'common' }
        - { role: volumio, tags: 'volumio' }

common will do the following:
- install and start ntp service
- set timezone to Europe/Amsterdam
- install and start cron service
- prevent ssh login without key-pair
- install ssmtp, mailutils and bzip2
- copy a new motd from template, using fqdn
- copy a new ssmtp.conf from template using group_vars
- copy some mail text files ans script files from templates using group_vars

volumio will do the following:
- replace the volumio logo for the web interface
- change colours in the stylesheet to match Digital Hifi colours
- add My Web Radiostations for NL



License
-------

GPL

Author Information
------------------

Nico Oosterwijk < nico@digitalinfo.nl >

