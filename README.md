# Ansible Galaxy role for install and configure unbound package.

![Build Status](https://github.com/leadlineit/ansible-role-unbound/actions/workflows/ansible-galaxy-ci.yml/badge.svg)
[![Galaxy Role](https://img.shields.io/badge/Ansible--Galaxy-leadlineit.unbound-blue.svg?logo=ansible&logoColor=white)](https://galaxy.ansible.com/leadlineit/unbound/)

This role helps to install and configure unbound package.

Supported OSes
--------------
- Debian 12 (bookworm)
- Debian 11 (bullseye)
- Debian 10 (buster)
- Debian 9 (stretch)

Requirements
------------

This role requires Ansible 2.11 or higher.

Role Variables
--------------

```yaml
---
unbound_configuration:
  - verbosity: 1
  - do-ip4: "yes"
  - do-ip6: "no"
  - do-udp: "yes"
  - do-tcp: "yes"
  - cache-min-ttl: 60
  - cache-max-ttl: 86400
  - num-threads: "{{ ansible_processor_count }}"
  - so-reuseport: "yes"
  - pidfile: "/var/run/unbound.pid"
  - logfile: "/var/log/unbound/unbound.log"
  - tls-cert-bundle: "/etc/ssl/certs/ca-certificates.crt"
  - root-hints: /etc/unbound/root.hints

unbound_control_configuration:
  - control-enable: "yes"
  - control-interface: 127.0.0.1

unbound_zone_name: "default"
unbound_only_zones: false

unbound_interfaces:
  - 127.0.0.1

unbound_access_control:
  - 127.0.0.1 allow

unbound_private_address:
  - 10.0.0.0/8
  - 172.16.0.0/12
  - 192.168.0.0/16
  - 169.254.0.0/16
  - "fd00::/8"
  - "fe80::/10"

unbound_domains: {}

unbound_domains_with_reverses: []

unbound_inventory_domain: {}

unbound_local_zone_type: {}
unbound_local_zone: []

unbound_default_local_zone: "static"

unbound_inventory_domain_with_reverse: true

unbound_zones:
  - name: "default"

unbound_forward_zone_active: true
unbound_forward_zone_configuration:
  - forward-tls-upstream: "yes"
unbound_forward_zone:
  # cloudflare resolvers
  - "1.1.1.1@853#cloudflare-dns.com"
  - "1.0.0.1@853#cloudflare-dns.com"

  # google resolvers
  - "8.8.8.8@853#dns.google"
  - "8.8.4.4@853#dns.google"

  # quad9 resolvers
  - "9.9.9.9@853#dns.quad9.net"
  - "149.112.112.112@853#dns.quad9.net"

unbound_resolvconf: false

```

A part of this variables are optional, if you omit them the values above will be used (default).

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
