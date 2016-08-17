Check-MK-Agent Ansible role
===========================

[![Ansible Galaxy](http://img.shields.io/badge/ansible--galaxy-HanXHX.check--mk--agent-blue.svg)](https://galaxy.ansible.com/list#/roles/4399) [![Build Status](https://travis-ci.org/HanXHX/ansible-check-mk-agent.svg?branch=master)](https://travis-ci.org/HanXHX/ansible-check-mk-agent) 

Install and configure check-mk-agent for Debian based systems.

Requirements
------------

- This role uses xinetd services. It doesn't manage systemd equivalent (or other inetd service). PR welcomed.
- Active support for Debian system. It should work on Ubuntu.
- On Debian Jessie, [check-mk-agent](https://packages.debian.org/jessie-backports/check-mk-agent) is only available on [backports repository](http://backports.debian.org/). You must install it before launching this role.

Role Variables
--------------

- `mk_port`: TCP port to listen
- `mk_only_from`: IP list who can call service. Default: empty list = all.
- `mk_inetd_daemon`: default is xinetd, other systems will be managed later.
- `mk_disable`: disable inetd service

Dependencies
------------

None.

Example Playbook
----------------

    - hosts: servers
      vars:
        mk_only_from:
          - mymonitoring.mydomain.tld
          - mymonitoring-slave.mydomain.tld
          - 127.0.0.1
      roles:
         - { role: HanXHX.check-mk-agent }

License
-------

GPLv2

Author Information
------------------

- Twitter: [@hanxhx_](https://twitter.com/hanxhx_)
