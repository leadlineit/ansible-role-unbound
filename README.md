# Ansible Role for Unbound package

![Build Status](https://github.com/leadlineit/ansible-role-unbound/actions/workflows/ansible-galaxy-ci.yml/badge.svg)
[![Galaxy Role](https://img.shields.io/badge/Ansible--Galaxy-leadlineit.unbound-blue.svg?logo=ansible&logoColor=white)](https://galaxy.ansible.com/leadlineit/unbound/)

This role helps to for install and configure Unbound package on a Debian (stretch/buster/bullseye).

Requirements
------------

This role requires Ansible 2.11 or higher.

Role Variables
--------------

```yaml
---
zabbix_agent_server: 127.0.0.1
zabbix_agent_listen_port: 10050
zabbix_agent_listen_ip: 0.0.0.0
zabbix_agent_psk: 6c4ccf50bacdb3486f141ba1112e4a46  # openssl rand -hex 16/(32)
zabbix_agent_psk_identity: localhost
zabbix_agent_plugins:
    - name: name_of_some_plugin
      parameters:
        key: some_key_for_plugin
        value: some_value_for_plugin
```

All variables are optional, if you omit them the values above will be used (default).

Dependencies
------------

None.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

```yaml
- hosts: servers
  roles:
    - { role: leadlineit.unbound, tags: unbound }
```

License
-------

MIT

Author Information
------------------

This role was created by Stas Stavnichuk.
