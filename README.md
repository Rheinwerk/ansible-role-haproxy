[![Build Status](https://github.com/Rheinwerk/ansible-role-haproxy/actions/workflows/ci.yml/badge.svg)](https://github.com/Rheinwerk/ansible-role-haproxy/actions/workflows/ci.yml)

Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should
be mentioned here. For instance, if the role uses the EC2 module, it may be a
good idea to mention in this section that the boto package is required.

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`):

```yaml
_haproxy:
  use_default_config: "yes"
  use_external_repo: true
  instance_name: "demo-haproxy"
  version: "2.8*"
  admin:
    user: "admin"
    password: "this-is-secret"
    binds:
      - ip: "0.0.0.0"
        port: 8404
  error_files: []
```

- `use_default_config`: Whether to use the default HAProxy configuration template
- `use_external_repo`: Whether to add external HAProxy repositories (PPA for Ubuntu, haproxy.debian.net for Debian). Set to `false` to use distribution default repositories instead. Default: `true`
- `instance_name`: Name of the HAProxy instance
- `version`: HAProxy version to install (supports wildcards like "2.8*")
- `admin`: Admin interface configuration
  - `user`: Admin username
  - `password`: Admin password
  - `binds`: List of IP/port bindings for admin interface
- `error_files`: Custom error files (optional)
- `ssl_certs`: SSL certificates to install (optional)

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in
regards to parameters that may need to be set for other roles, or variables that
are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

```yaml
- hosts: servers
  roles:
    - { role: ansible-role-haproxy, _haproxy: "{{ HAPROXY }}" }
```

To disable external repositories and use distribution defaults:

```yaml
- hosts: servers
  vars:
    _haproxy:
      use_external_repo: false
      version: "2.8*"
      # ... other config
  roles:
    - ansible-role-haproxy
```

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a
website (HTML is not allowed).
