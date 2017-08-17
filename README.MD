linux_helper
=============

Various Linux deployments.

Requirements
---------------

* Ansible 2.2;
* [python-netaddr](//docs.ansible.com/ansible/playbooks_filters_ipaddr.html);

Example configuration
-----------------------

```yaml
---
# Set system locales. Order is important for LANG environmental, i.e. only last
# record is your locale. Example:
linux_helper_locale:
- locale: 'ru_RU'
  charset: 'UTF-8'
- locale: 'en_US'
  charset: 'UTF-8'
# Generate locales for ru_RU and en_US locales, if you want to set LANG env.
# This sets your env LANG to 'en_US.UTF-8'.
linux_helper_set_langs: 'true'

# Static table lookup for hostnames.
linux_helper_hosts:
# IP address.
- address: '192.168.0.193'
# List of aliases.
  aliases:
  - 'home'
  - 'mirror.archlinux.org'
```
