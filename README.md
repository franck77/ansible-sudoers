# Simple sudoers role

This role installs sudo package, ensure that /etc/sudoers.d included and
Create or remove sudoers files in /etc/sudoers.d/
Allow users and groups to run command as root without Password.

## Variables

 * sudoers_filename - file name in /etc/sudoers.d (required)
 * sudoers - A dictonary of users who have sudo access and to what users they have
   permission to execute commands as. Use '%foo' to specify that users in a given
   group have sudo access.
   * defaults: []
 * sudoers_nopasswd - if set, NOPASSWD is added to all sudoers entries. Use this
   when users don't have passwords set.
   * default: true
 * sudoers_remove - if enabled, remove /etc/sudoers.d/{{ sudoers\_filename }} instead
   of create.
   * default: false

## Example playbook
```
---
- hosts: <my_hosts>
  vars:
    sudoers:
      - name: "<file_name>"
        cmd: "<command_list_allow_without_PASSWORD>"
        users:
          - "<user1>"
          - "<user2>"
          - ...
        groups:
          - "<group1>"
          - "<group2>
          - ...
  roles:
    - ansible-sudoers
```
