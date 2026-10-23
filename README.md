Ansible Role: Containers
========================

[![CI](https://github.com/hadret/ansible-role-containers/actions/workflows/ci.yaml/badge.svg?branch=main)](https://github.com/hadret/ansible-role-containers/actions/workflows/ci.yaml?query=branch%3Amain)

An Ansible role that spins up an array of [Docker](https://docker.com)
containers on Linux. It can additionally handle arrays of Docker registries
and networks.

Requirements
------------

Docker needs to be in place in order for this role to work. Additionally, the
`community.docker` collection and Python module
[docker](https://pypi.org/project/docker) are needed (i.e. Docker SDK for
Python).

Ansible Core 2.17 or newer is required by current `community.docker` releases.

```shell
ansible-galaxy collection install community.docker
```

Role Variables
--------------

All available variables are arrays (`containers`, `networks` and `registries`).
They are empty by default but you can find one example for each in
[defaults/main.yml](defaults/main.yml).

Dependencies
------------

The following roles are not a hard dependencies, hence they are not mentioned
in the [meta/main.yml](meta/main.yml) file. Reason for that geerlingguy.docker
and geerlingguy.pip is to just ensure that the Docker daemon and Docker Python
SDK is present (as both of these are hard dependencies).

- [geerlingguy.pip](https://github.com/geerlingguy/ansible-role-pip)
- [geerlingguy.docker](https://github.com/geerlingguy/ansible-role-docker)

Example Playbook
----------------

```
- hosts: all

vars:
  pip_package: python-pip
  pip_install_packages:
    - name: docker

  networks:
    - name: network-1

  containers:
    - name: hello-1
      image: "hello-world"
      state: started
      restart_policy: always
      networks:
        - name: network-1
    - name: hello-2
      image: "hello-world"
      state: started
      restart_policy: always
      networks:
        - name: network-1

roles:
  - geerlingguy.pip
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
