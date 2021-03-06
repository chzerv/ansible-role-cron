# Ansible Role: Cron

![Test and release.](https://github.com/chzerv/ansible-role-cron/workflows/Test%20and%20release./badge.svg?branch=master)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Ansible Role](https://img.shields.io/ansible/role/50230?color=dodgerblue)](https://galaxy.ansible.com/chzerv/cron)

This role installs [cron](https://wiki.archlinux.org/index.php/Cron) and schedules jobs on a Linux system.

## Requirements

None.

## Role Variables

```yaml
cron_backup_original_crontab: true
```

> Whether to backup the original crontab before modifying it.

```yaml
cron_jobs: []
# cron_jobs:
#   - name: Foo
#     minute: "0"
#     hour: "0"
#     day: "*"
#     month: "4"
#     weekday: "*"
#     job: "foo.sh"
#     state: present
#     user: "{{ ansible_user }}"
```

> A list of options in order to schedule the specified job. These options are:
>
> - `name`: The name of the job. (**required**)
> - `minute`: Minute when the job will be run. Possible values are between 0-59. (**optional**)
> - `hour`: Hour of the day when the job will be run. Possible values are between 0-23. (**optional**)
> - `day`: Day of the month the job will be run. Possible values are between 1-31. (**optional**)
> - `month`: Month the job will be run. Possible values are between 1-12. (**optional**)
> - `weekday`: Day of the week the job will be run. Possible values are between 0-6. (**optional**)
> - `special_time`: Can be used instead of hour, minute etc.
>   Possible values are: `annually`, `daily`, `hourly`, `monthly`, `reboot`, `weekly`, `yearly`. (**optional**)
> - `job`: The script/command etc to execute. (**required**)
> - `state`: Possible values are: `present`, which will ensure the job is present, and `absent` which will delete the job. Defaults to `present`. (**optional**)
> - `user`: Which user's crontab to modify. Defaults to the _root_ user. (**optional**)

> **Note:** If any of the (optional) options are not specified they will be omitted.

## Dependencies

None.

## Example Playbook

```yaml
- hosts: server
  vars:
    cron_jobs:
      - name: Test
        minute: "0"
        hour: "5,2"
        job: "/path/to/foo.sh"
        state: present
      - name: Test 2
        state: absent

  roles:
    - { role: chzerv.cron }
```

## License

MIT / BSD

## Author Information

Xristos Zervakis
