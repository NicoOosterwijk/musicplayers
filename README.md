MusicPlayers
============

Ansible will install the files required by Digital Hifi to publish its own styling to the Volumio GUI. It will also install additional services like ssmtp, cron and ntp. De MusicPlayer will be setup as device for *SqueezeBox* Server (LMS) and as device for *Roon* Server.

Requirements
------------
- Volumio 2.x should be fully installed
- The sshd should be enabled (go to http://volumio.local/dev to enable it)

Role Variables
--------------

common: (group_vars)
-------
- ntpserver: URI of the NL NTP server
- mail_to: should be a valid e-mail address, default to "noosterwijk@hotmail.com" 
- mail_from: should be a valid mail-account from your mail-server. Default to: "nico.oosterwijk@ziggo.nl"

volumio: (group_vars)
--------
- radiostation_uri: the URI for the webradio stream
- airplay_password: to be used as password for AirPlay service
- stylesheet_digitalhifi_color: color to be used in stylesheet
- stylesheet_volumio_color: default color of Volumio
- squeezelite_server_address: server IP address for LMS


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
- set player as Roon device
- set player as Squeezebox (LMS) device
- put a password on AirPlay

License
-------

GPL

Author Information
------------------

Nico Oosterwijk < nico@digitalinfo.nl >

