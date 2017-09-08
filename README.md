Ansible Role: FirewallD
=========

Installs and configures FirewallD on Centos

This role must be run with become: true.

As one might easily notice, the role currently only supports a subset of configuration possibilities in FirewallD (and its ansible module).

Requirements
------------

None

Role Variables
--------------

    firewalld_testing:      false
    firewalld_zone:         "public"
    firewalld_services:
      - service: ssh
      - service: http
        state: disabled
    firewalld_ports:
      - port: 80
        protocol: tcp
        state: disabled
    firewalld_richrules:
      - rule: 'rule family="ipv4" source address="128.220.8.58/32" source-port port="8080" protocol="tcp" log prefix="jetty" level="info" accept'
        state: disabled

Dependencies
------------

None

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: firewalld, become: true }

License
-------

CC0

Author Information
------------------

Drew Heles
