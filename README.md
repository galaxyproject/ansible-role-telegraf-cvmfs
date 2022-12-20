galaxyproject.telegraf_cvmfs
============================

Monitor [CVMFS][cvmfs] servers with [Telegraf][telegraf]

[cvmfs]: https://cernvm.cern.ch/fs/
[telegraf]: https://www.influxdata.com/time-series-platform/telegraf/

Requirements
------------

This role does not install or configure Telegraf core functionality, but is dependent on [dj-wasabi.telegraf][dj-wasabi-telegraf], which can be used for this purpose.

[dj-wasabi-telegraf]: https://galaxy.ansible.com/dj-wasabi/telegraf

Role Variables
--------------

See [defaults/main.yml](defaults/main.yml).

Lists `telegraf_cvmfs_check_servers.hosts` and `telegraf_cvmfs_check_servers.repos` or `telegraf_cvmfs_check_servers.combined` are required if you want the role to do anything.

Dependencies
------------

Although not a hard dependency (since this role runs *before* it), without [dj-wasabi.telegraf][dj-wasabi-telegraf], this role will only install the check script and will not configure Telegraf. This role also depends on the restart handler from dj-wasabi.telegraf.

Example Playbook
----------------

```yaml
- hosts: all
  vars:
    telegraf_cvmfs_check_servers:
      hosts:
        - cvmfs1.example.org
      repos:
        - repo1.example.org
        - repo2.example.org
      combined:
        - host: cvmfs0.example.org
          repos:
            - repo1.example.org
  roles:
    - galaxyproject.telegraf_cvmfs
    - dj-wasabi.telegraf
```

License
-------

MIT

Author Information
------------------

- Helena Rasche (@hexylena)
- Nate Coraor (@natefoo)
