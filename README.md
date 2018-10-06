MusicPlayers
============

Ansible will install the files required by Digital Hifi to publish its own styling to the Volumio GUI. It will also install additional services like ssmtp, cron and ntp. 

Requirements
------------
- Volumio 2.x should be fully installed
- The sshd should be enabled (go to http://volumio.local/dev to enable it)
- Match the MusicPlayers IP addresses to the inventory file

Role Variables
--------------

common: (defaults)
-------
- ntpserver: URI of the NL NTP server
- mail_to: should be a valid e-mail address, PLEASE UPDATE VARS in DEFAULTS! 
- mail_from: should be a valid mail-account from your mail-server. PLEASE UPDATE VARS in DEFAULTS!

volumio: (defaults)
--------
- radiostation_uri: the URI for the webradio stream
- airplay_password: to be used as password for AirPlay service
- stylesheet_digitalhifi_color: color to be used in stylesheet
- stylesheet_volumio_color: default color of Volumio


Dependencies
------------

A known public key must exist on the MusicPlayer to be altered. This public key must match the private key in your GitLab account.

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
- copy a new ssmtp.conf from template using variables
- copy some mail text files ans script files from templates using variables

volumio will do the following:
- replace the volumio logo for the web interface
- change colours in the stylesheet to match Digital Hifi colours (using variables)
- change the GUI title
- replace the link to Volumio shop to Digital Hifi website
- add My Web Radiostations for NL using variables
- put a password on AirPlay

License
-------

GPL

Author Information
------------------

Nico Oosterwijk < nico@digitalinfo.nl >

