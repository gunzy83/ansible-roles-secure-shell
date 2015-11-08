ansible-roles-secure-shell
==========================

**ansible-roles-secure-shell** is a pair of modules for configuration of SSH with security as a focus. This is heavily inspired by the following blog post by [@stribika](https://github.com/stribika):

[https://stribika.github.io/2015/01/04/secure-secure-shell.html](https://stribika.github.io/2015/01/04/secure-secure-shell.html)

Installation
============

Clone the repo:

    $ git clone https://github.com/gunzy83/ansible-roles-secure-shell.git ~/projects/ansible-roles-secure-shell

Then add the path to your **ansible.cfg** file:

    roles_path = ~/projects/ansible-roles-secure-shell

Usage
=====

    ---
    - name: Clients only without Github support
      hosts: clients
      become: yes

      roles:
        - { role: ssh-client, ssh_client_github: no }

    - name: Servers only with compatibility WinSCP, Eclipse etc
      hosts: servers
      become: yes

      roles:
        - { role: ssh-server, ssh_server_compat: yes }

    - name: Both Clients and Servers
      hosts: combined
      become: yes

      roles:
        - ssh-server
        - ssh-client

Limitations
===========

* Does not create new ssh keys for your user or distribute them. This is a user concern so I am implementing this in another role.
* Does not implement Tor hidden services - I am mainly using this role on a LAN at this point, might add this to some VPS deployments I have planned but would not be useable at work.

Future Plans
============

* Include Tor hidden services
* Travis CI tests

License
=======

**ansible-roles-secure-shell** is provided under the terms of [The MIT License](http://opensource.org/licenses/MIT)

Copyright &copy; 2015, [Ross Williams](mailto:gunzy83au@gmail.com)


