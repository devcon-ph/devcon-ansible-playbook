# DevCon Ansible Playbook

This is an [Ansible](http://ansible.com/) playbook to recreate the [DevCon](http://devcon.ph/) server.

## What this installs

* DevCon web page
* Old static pages (e.g. Summit)
* Analytics software (Piwik)

## Setup

    ansible-playbook -i hosts devcon.yml
