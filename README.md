# Ansible Role: Cron

This role installs [cron](https://wiki.archlinux.org/index.php/Cron) and schedules jobs on a Linux system.

## Requirements

None.

## Role Variables

## Dependencies

None.

## Example Playbook

```yaml
- hosts: server
  vars_files:
    - vars/main.yml

  roles:
    - { role: chzerv.cron }
```

The `vars/main.yml` file:

```yaml
WIP
```

## License

MIT / BSD

## Author Information

Xristos Zervakis
