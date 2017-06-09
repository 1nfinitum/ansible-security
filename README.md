Ansible Role: Security
=========
[![Build Status](https://travis-ci.org/tenequm/ansible-security.svg?branch=master)](https://travis-ci.org/tenequm/ansible-security)

Role for applying security configurations for Ubuntu Xenial including security autoupdates.

Role Variables
--------------
```
security_fail2ban_enabled: '' # Boolean
```
Wether to install/enable fail2ban. By default it's turned off, to enable set it to `true`, note that it will work only on Debian type machine, while it uses `apt` package for installation. You might not want to use fail2ban if you're already using some other service for login and intrusion detection. By default it's set to `false`.
```
security_autoupdate_blacklist: []
```
List of packages that should not be automatically updated during automatic security updates.
### SSH configurations
```
security_enable_ssh_config: '' # Boolean
```
Whether to enable SSH configurations or not. The following configurations would accomplish only if it will be set to `true`. By default it's set to `false`.
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

Example Playbook
----------------
Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: tenequm.security, x: 42 }

License
-------
MIT

Author Information
------------------
This role was created in 2017 by [Mykhaylo Kolesnik](http://github.com/tenequm).
