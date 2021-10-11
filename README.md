Ansible Role: FirewallD
=========

*NOTE: This role is now tagged for deletion and has been replaced with https://github.com/jhu-library-devops/ansible-role-firewalld.*

Installs and configures FirewallD on Centos

This role must be run with `become: true`.

As one might easily notice, the role currently only supports a subset of configuration possibilities in FirewallD (and its ansible module).

Requirements
------------

None

Role Variables
--------------

    firewalld_testing:          false
    firewalld_update_packages:  "{{ update_packages | default(false) }}"
    firewalld_zone:             "public"
    firewalld_services: []
      # - service: ssh
      # - service: http
      #   state: disabled
    firewalld_ports: []
      # - port: 80
      #   protocol: tcp
      #   state: disabled
    firewalld_richrules: []
      # - rule: 'rule family="ipv4" source ipset="whitelist" port port="8080" protocol="tcp" log prefix="port-access-allowed" level="info" limit value="1/m" accept'
      #   state: disabled
      # - rule: 'rule family="ipv4" source NOT ipset="whitelist" port port="8080" protocol="tcp" log prefix="port-access-denied" level="info" limit value="1/m" reject'
      #   state: disabled
      # - rule: 'rule family="ipv4" source ipset="blacklist" log prefix="blacklist-access-denied" level="info" limit value="1/m" reject'
      #   state: disabled
    firewalld_ipsets: []
      # - name: whitelist
      #   ips:
      #     - "63.245.215.20"
      #     - "69.50.232.54"
      # - name: blacklist
      #   ips:
      #     - "172.217.7.142"
      #     - "31.13.69.228"

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

[CC0](http://creativecommons.org/publicdomain/zero/1.0/)

Author Information
------------------

Drew Heles
