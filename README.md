# Simple sudoers role

This role installs sudo package, ensure that /etc/sudoers.d included and
Create or remove sudoers files in /etc/sudoers.d/
Allow users and groups to run command as root without Password.

## Variables

 * sudoers - A dictonary of users, groups, commands, filename
   * defaults: []
 * sudoers.users - List of users who can run command without password as root
 * sudoers.groups - List of group who can run command without password as root
 * sudoers.cmd - List of command who can run the users and groups without password (separated by ",")
 * sudoers.remove - if enabled, remove /etc/sudoers.d/{{ sudoers.name }} instead
   of create.
   * default: false

## Example playbook 
```
---
- hosts: <my_hosts>
  vars:
    sudoers:
      - name: "<file_name>" ### ADD NEW SUDOERS
        cmd: "<command_list_allow_without_PASSWORD>"
        users:
          - "<user1>"
          - "<user2>"
          - ...
        groups:
          - "<group1>"
          - "<group2>
          - ...
      - name: "<file_name>" ### REMOVE OLD SUDOERS
        remove: "true"
  roles:
    - ansible-sudoers
```
