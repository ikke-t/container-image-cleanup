Container Cleanup
=================

Cleans up all unused container images from host. Role sets up cron job based on if podman or docker is installed.

Requirements
------------

Role checks if either Podman or Docker is installed on host before installing cronjob.

Role Variables
--------------

There are variables in defaults/main.yml for cron hour and minute options,
as well as path to binaries for docker and podman to check for.

Dependencies
------------

No dependencies.

Example Playbook
----------------

```
- name: periodicly clean up unused containers
  hosts: all
    roles:
        - container-cleanup
```

License
-------

GPLv3

Author Information
------------------

Ilkka Tengvall
