Ansible Role: Containers
========================

An Ansible role that spins up an array of [Docker](https://docker.com)
containers on Linux. It can additionally handle an array of Docker registries
to login to.

Requirements
------------

Docker needs to be in place in order for this role to work.

Role Variables
--------------

Available variables are both arrays: `containers` and `registries`. They are
empty by default but you can find one example for each in
[defaults/main.yml](defaults/main.yml).

Dependencies
------------

- [geerlingguy.docker](https://github.com/geerlingguy/ansible-role-docker)

Example Playbook
----------------

```
- hosts: all
  roles:
     - geerlingguy.docker
     - hadret.containers
```

Credits
-------

All of the `molecule` tests and CI configuration are based on work of
[geerlingguy](https://github.com/geerlingguy).

License
-------

MIT

Author Information
------------------

This role was somewhat assembled in 2019 by [Filip Chabik](https://chabik.com).
