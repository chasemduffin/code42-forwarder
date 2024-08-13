code42-forwarder
=========

This role installs the Code42 CLI and configures cron to forward security logs to a SIEM tool.

More information can be found at https://support.code42.com/Administrator/Cloud/Monitoring_and_managing/Integrate_with_a_SIEM_tool_using_the_Code42_command-line_interface

Requirements
------------

- A subscription to the Code42 Insider Threat Platform
- A password authenticated user in your Code42 org with the required permissions outlined in the Code42 documentation
- A RHEL-like OS (for yum)

Role Variables
--------------

- begin: Begin date: the beginning of the date range in which to look for events

  Use YYYY-MM-DD (UTC) or YYYY-MM-DD HH:MM:SS (UTC + 24-hour time) format, or shorthand date-range strings for days, hours, and minute intervals going back from the current time (for example, 30d, 24h, 15m.

  Begin date is required. Example: 

  code42 security-data print -b 2020-04-28 
- destination: Send to a server address, for example, "https://syslog.example.com:514"
- username: The username of your Code42 user, for example, "log_forwarder"
- profile: The desired name of your CLI profile
- server: Your Code42 server URL, for example "https://www.console.us.code42.com/"
- secret: Your encrypted Code42 password

Example Playbook
----------------

`ansible-playbook -i "0.0.0.0," -u centos run-role.yml --vault-password-file=~/.ansible_vault_password`

```
---

- name: Run the specified role against the specified remote host
  hosts: servers
  tasks:

    - name: run the following configuration role
      include_role:
        name: code42-forwarder
```


License
-------

BSD-3-Clause

Author Information
------------------

- cmd.bio
