Ansible Role: Security
=========

Role for applying security configurations for Ubuntu Xenial.

Requirements
------------
This role requires only root access for accomplishing its operations, so either run it in a playbook with a global `become: yes`, or invoke the role in your playbook like:

    - hosts: localhost
    roles:
      - role: 1nfinitum.ssh-users

Role Variables
--------------

The following variables are obtaining basic SSH security configurations to keep your server safer. By default these configurations is turned `off`, to prevent critical changes for existing servers, so if you want to use it - set `enable_ssh_config` to `true` in your `vars` or vars file you use.
```
ssh_port: 22
```
The port through which you'd like SSH to be accessible. The default is port 22, but if you're operating a server on the open internet, and have no firewall blocking access to port 22, you'll quickly find that thousands of login attempts per day are not uncommon. You can change the port to a nonstandard port (e.g. 2849) if you want to avoid these thousands of automated penetration attempts.
```
ssh_password_authentication: "no"
ssh_permit_root_login: "no"
ssh_use_dns: "no"
```
Security settings for SSH authentication. It's best to leave these set to "no", but there are times (especially during initial server configuration or when you don't have key-based authentication in place) when one or all may be safely set to 'yes'.
```
fail2ban_enabled: false
```
Wether to install/enable fail2ban. By default it's turned off, to enable set it to `true`, note that it will work only on Debian type machine, while it uses `apt` package for installation. You might not want to use fail2ban if you're already using some other service for login and intrusion detection.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: 1nfinitum.security, x: 42 }

License
-------

MIT

Author Information
------------------

This role was created in 2017 by [Mykhaylo Kolesnik](http://github.com/1nfinitum).
