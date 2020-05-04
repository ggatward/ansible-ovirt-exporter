# Ansible Role: ovirt_exporter

## Description

Deploy prometheus [ovirt_exporter](https://github.com/terrycain/ovirt_exporter) using ansible.

## Requirements

- Ansible >= 2.9 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `ovirt_exporter_version` | 0.9.0 | ovirt_exporter package version |
| `ovirt_exporter_web_listen_address` | "0.0.0.0:9496" | Address on which ovirt_exporter will listen |
| `ovirt_exporter_scrape_uri` | https://localhost/ovirt-engine/api/ | Address of the oVirt engine API |
| `ovirt_exporter_ssl_verify` | true | Verify oVirt engine SSL certificate |
| `ovirt_exporter_user` | admin@internal | User to access oVirt engine API |
| `ovirt_exporter_password` | 'ChangeMe' | Password of the user accessing oVirt engine API |
| `ovirt_exporter_password_file` | '' | Location of file containing Password of the user accessing oVirt engine API (optional) |
| `ovirt_exporter_include_disks` | true | Include Storage Domain metrics |
| `ovirt_exporter_include_network` | true | Include Network metrics |
| `ovirt_exporter_include_snapshots` | true | Include Snapshot metrics |
| `ovirt_exporter_config_flags_extra` | {} | Additional configuration flags passed at startup to ovirt_exporter binary |


## Example

### Playbook

Use it in a playbook as follows:
```yaml
- hosts: all
  roles:
    - ovirt_exporter
  vars:
    ovirt_exporter_scrape_uri: https://ovirt-engine.example.com/ovirt-engine/api/
    ovirt_exporter_user: 'prometheus@internal'
    ovirt_exporter_password_file: /root/ovirt_password
```
