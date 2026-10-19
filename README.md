[![Build Status](https://github.com/Rheinwerk/ansible-role-haproxy/actions/workflows/ci.yml/badge.svg)](https://github.com/Rheinwerk/ansible-role-haproxy/actions/workflows/ci.yml)

Role Name
=========

Installs HAProxy from haproxy.debian.net (Debian) or the vbernat PPA (Ubuntu), pinned to one
series, with a systemd unit per instance name.

Requirements
------------

None.

Role Variables
--------------

Every setting is one variable with a default in `defaults/main.yml`; set only the ones that differ.

| Variable | Default |
|---|---|
| `_haproxy_instance_name` | `haproxy`: configuration directory `/etc/<instance>`, unit `<instance>.service`, handler `Reload haproxy <instance>` |
| `_haproxy_version` | apt version pattern of the series: `"2.8*"`, on Debian 13 (trixie) `"3.2*"` because haproxy.debian.net has no 2.8 there (`vars/main.yml`) |
| `_haproxy_use_default_config` | `false`; `true` renders the role's demo configuration, which exists for the instance name `demo-haproxy` only |
| `_haproxy_admin` | stats endpoint of the demo configuration: user `admin`, bind `127.0.0.1:8404`; add `password` with the demo configuration |
| `_haproxy_ssl_certs` | no default; `{name: {filename, data}}` with base64 PEM data, installed to `/etc/<instance>/ssl` |

`_haproxy_version` selects the haproxy.debian.net suite (Debian) or the vbernat PPA (Ubuntu) and pins
the package to it. Until v1.5.1 the role took one `_haproxy` dict with these keys instead.

Dependencies
------------

None.

Example Playbook
----------------

Only the instance name differs from the defaults here:

    - hosts: servers
      vars:
        _haproxy_instance_name: "haproxy-public"
      roles:
         - { role: haproxy, tags: [ 'haproxy' ] }

The play must provide the handler `Reload haproxy <instance name>`.

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a
website (HTML is not allowed).
