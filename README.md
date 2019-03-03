Container Image Cleanup
=======================

Periodicly cleans up all unused container images from host. Role sets up cron
job based on whether podman or docker is installed.

Requirements
------------

Role checks if either Podman or Docker is installed on host before installing cronjob.

Role Variables
--------------

There are variables in defaults/main.yml for timing of cronjob,
as well as path to binaries for docker and podman to check for.


* **podman_prune_cronjob_special_time**  
  see special_time options https://docs.ansible.com/ansible/latest/modules/cron_module.html
* **docker_prune_cronjob_special_time**  
  see special_time options https://docs.ansible.com/ansible/latest/modules/cron_module.html
* **podman_prune_opts**  
  podman system prune options, e.g. "--all --force"
* **docker_prune_opts:**  
  docker image prune options, e.g. "--all --force"
* **podman_path:**  
  where to look for podman executable, e.g: /usr/bin/podman
* **docker_path:**  
  where to look for docker executable, e.g: /usr/bin/docker


Dependencies
------------

No dependencies.

Example Playbook
----------------

```
- name: periodicly clean up unused containers
  hosts: all
  roles:
    - role: container_image_cleanup
      vars:
        podman_prune_cronjob_special_time: daily
        docker_prune_cronjob_special_time: weekly
        podman_prune_opts: "--all --force"
        docker_prune_opts: "--all --force"
        podman_path: /usr/bin/podman
        docker_path: /usr/bin/docker
```

License
-------

GPLv3

Author Information
------------------

Ilkka Tengvall, ilkka.tengvall@iki.fi
