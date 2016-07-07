docker
=========

Install the latest docker on Fedora.

Based on https://docs.docker.com/engine/installation/linux/fedora/

Requirements
------------

Must be run on a Fedora Node.

Role Variables
--------------

| Name | Possible Values | Default Value |
|----------|-----------------|-------------|
| docker_testing | boolean | False |
| docker_selinux | enforcing, permissive, disabled | enforcing |

Dependencies
------------

On Fedora 23+, the following packages should be installed:

- ansible
- python2-dnf
- libselinux-python

This is due to recent Fedora systems making the switch to Python3 and
Ansible still relies on Python2.

Example Playbook
----------------

How to install the latest Docker on Fedora systems:

    - hosts: servers
      roles:
        - ksylvan.docker

Set the `docker_testing`
variable to `true` in order to use the `testing` repository instead of the
`main` repository.

Note: Fedora 24 currently has problems with SELinux. This role will add
a local policy in `/usr/local/selinux/` called `hack-docker` which fixes this. If you prefer not to do this, then set `docker_selinux` to
`permissive` and the `hack-docker` policy will not be installed.

See [Cannot start docker engine
due to SELinux](https://github.com/docker/docker/issues/23981) for details.

License
-------

GPLv3

Author Information
------------------
*Kayvan Sylvan <kayvan.sylvan@gmail.com> -
[https://github.com/ksylvan](https://github.com/ksylvan)*
