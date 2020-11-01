# ansible-role-server

## Install
```
ansible-galaxy install tseho.server
```

See [defaults](defaults/main.yml) for overridable options.

## iptables

iptables are configured by default.

If you want to add one, see [iptables_module](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/iptables_module.html) and don't forget to trigger `Save iptables`.

```
- iptables:
    chain: INPUT
    action: insert
    ...
  notify: Save iptables
```

## ACL on files

If you want to allow an user to write on a directory or file, you can use the role:

```
tasks:
 - import_role:
     name: tseho.server
     tasks_from: acl
   vars:
     server_writable_paths:
       - path: "/var/foo"
         user: "www-data"
```
