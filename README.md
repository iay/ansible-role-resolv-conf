# Ansible role to configure `/etc/resolv.conf`

The simplest possible Ansible role to allow configuration of the `/etc/resolv.conf` on Debian systems.

This role does not attempt to communicate with other services on the host, so it won't for example
work correctly in a system using `systemd-resolved` for name resolution.

## Requirements

None.

## Role Variables

`resolv_conf_search` is an optional list of domains to be used in the `search` option for the configuration.
If omitted, no `search` option will be included.

`resolv_conf_nameservers` is a list of strings representing DNS nameservers for the system. Each will
result in a `nameserver` option in the file. Defaults to the single `8.8.8.8` server.

## Dependencies

None.

## Example Playbook

```yaml
---
- name: Set up /etc/resolv.conf.
  hosts: all
  roles:
    - role: iay.resolv_conf
      resolv_conf_search:
        - example.org
      resolv_conf_nameservers:
        - '8.8.8.8'
        - '8.8.4.4'
```

## License

Apache 2.0

## Author Information

Copyright (C) 2024, [Ian A. Young](https://iay.org.uk/).
