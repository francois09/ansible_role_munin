MUNIN Ansible role
==================

Role to manage MUNIN. Works fine on `cron` strategy and nginx, some issues with `cgi` strategy, and no other http server configured for now.

Requirements
------------

No requirements

Role Variables
--------------

* `munin__install` For install only (default: False)
* `munin__configure` For configuration  (default: False)
* `munin__client_configure` For client-side configuration  (default: False)
* `munin__hostname` define the server_name for nginx
* `munin__webserver` Only "nginx" supported for now
* `munin__webserver_strategy` defines the html and graph page generation stragegy 
* `munin__email_notification` who should be notified
* `munin__main_group` Default server group (ie internal domain)
* `munin__use_ssl` Configure SSL (default: False)
* `munin__ssl_cert` Path of certificate file
* `munin__ssl_key` Path of certificate key file
* `munin__ssl_dhparam` Path of dhparam file
* `munin__ssl_includefile` Path of specific inclusion file



Dependencies
------------

None

Example Playbooks
-----------------

* With the following inventory vars for the server:
```
munin__install: True
munin__configure: True
munin__client_configure: True

munin__webserver: "nginx"

munin__webserver_strategy: "cron"

munin__hostname: "monitoring.example.org"

munin__email_notification: "alerts@example.org"
munin__main_group: "example.org"

```

* And for the nodes:
```
munin__client_configure: True
```

* You can run the following playbook:
```
- hosts: all
  name: "Run munin role"
  become: yes
  gather_facts: True
  roles:
    - role: munin

```

License
-------

GPL v3

Author Information
------------------

François TOURDE
