This is an [Ansible](http://www.ansible.com/home) role for installing
[Zabbix server](https://www.zabbix.com/documentation/2.0/manual/concepts/server).

You may also be interested in:

* an Ansible role for
  [Zabbix agent](https://github.com/dhruvbansal/zabbix-agent-ansible-role)
* an Ansible role for the
  [Zabbix frontend](https://github.com/dhruvbansal/zabbix-web-ansible-role)

# What it Does

## Software

Installs the `zabbix-server-mysql` package which provides the
following commands:

* `zabbix_server` -- Zabbix server
* `zabbix_get` -- used to get data from Zabbix agents via command-line

## Configuration & Logging

Creates the files:

* `/etc/zabbix/zabbix_server.conf` -- configuration file for Zabbix agent
* `/etc/logstash/conf.d/zabbix-server.conf` -- input file for logstash
* `/var/log/zabbix-server` -- log directory

## Services

Leaves a service `zabbix-server` running on port 10051.

# Usage

Use the role in a playbook like this:

```yaml
- hosts: all
  roles:
    - zabbix-server
```

Set the `zabbix_server_use_logstash` to `false` to skip the logstash
configuration.

## Variables

The following variables are exposed for configuration

* `mysql_root_password` -- the password for the MySQL root user
* `zabbix_database_host` -- host for the database
* `zabbix_database_port` -- port for the database
* `zabbix_database_username` -- username to connect to the database as
* `zabbix_database_password` -- password to connect to the database with
* `zabbix_database_name` -- name of the database
* `zabbix_server_use_logstash` -- set to `false` to skip logstash configuration
