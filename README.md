# Ansible Role: Cron

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
> - `minute`: (**optional**)
> - `hour`: (**optional**)
> - `day`: (**optional**)
> - `month`: (**optional**)
> - `weekday`: (**optional**)
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
