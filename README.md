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

All settings live in the `_haproxy` dictionary (see `defaults/main.yml`); passing
`_haproxy` replaces the whole dictionary.

`_haproxy.version` is the apt version pattern of the HAProxy series, e.g. `"3.2*"`. It
selects the haproxy.debian.net suite (Debian) or the vbernat PPA (Ubuntu) and pins the
package to it. The default is `"2.8*"`, except on Debian 13 (trixie), where
haproxy.debian.net has no 2.8 and the default is `"3.2*"` (`vars/main.yml`).

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in
regards to parameters that may need to be set for other roles, or variables that
are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables
passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: ansible-role-haproxy, _haproxy: "{{ HAPROXY }}" }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a
website (HTML is not allowed).
