Role Name
=========

minishift: Minishift

[![Build Status](https://travis-ci.org/cmihai-ansible/minishift.svg?branch=master)](https://travis-ci.org/cmihai-ansible/minishift)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.minishift](https://galaxy.ansible.com/devopstoolbox.minishift)

```bash
ansible-galaxy install devopstoolbox.minishift
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
minishift_packages_state: present
minishift_remove_packages: true
minishift_enable_service: true
minishift_enable_selinux: true
minishift_copy_templates: true
minishift_firewall_configure: true
minishift_firewall_rules:
  - service: ssh
  - port: 3389
minishift_users:
  - user: devops
    group: docker
minishift_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install minishift on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: minishift is configured
      import_role:
        name: devopstoolbox.minishift
      vars:
        minishift_packages_state: present
        minishift_remove_packages: true
        minishift_enable_service: true
        minishift_enable_selinux: true
        minishift_copy_templates: true
        minishift_firewall_configure: true
        minishift_firewall_rules:
          - service: ssh
          - port: 3389
        minishift_users:
          - user: devops
            group: docker
        minishift_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: minishift
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/crivetimihai)
