linux_helper
=============

Various Linux deployments.

Requirements
---------------

* Ansible 2.0;

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
# Generate locales for ru_RU and en_US locales, if you want to set LANG env:
linux_helper_set_langs: 'true'
# This sets your env LANG to 'en_US.UTF-8'.
```
