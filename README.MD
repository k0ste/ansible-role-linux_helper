# linux_helper

Various Linux deployments.

## Requirements

* Ansible 2.5+;

## Example configuration

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

linux_helper_modprobe:
- drop_exists: 'true'
  modprobes:
  - file_name: 'intel-mei'
    actions:
  # Create alias for 'mei', 'mei-me', 'mei-txe'
    - action: 'alias'
      wildcard: 'intel-mei'
      module: 'mei*'
  # Blacklist this modules
    - action: 'blacklist'
      module: 'intel-mei'
  # Set sequence options for module
  - file_name: 'intel-snd'
    actions:
    - action: 'options'
      module: 'snd_hda_intel'
      options:
      - 'power_save=1'
      - 'power_save_controller=N'
  # Set one option for module, as string
  - file_name: 'intel-iwl'
    actions:
    - action: 'options'
      module: 'iwlwifi'
      options: '11n_disable=8'
```
