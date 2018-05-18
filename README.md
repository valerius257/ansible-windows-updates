Windows Updates
===============

This role can be used to install Windows Updates and Hotfixes.

Requirements
------------

* Ansible 2.4
* [Prepared Windows System](http://docs.ansible.com/ansible/latest/user_guide/windows_setup.html)

Parameters
----------

* `windows_update_allowed`: Determines if installation of windows updates is allowed.
* `windows_reboot_allowed`: Determines if reboot of machines after updates installation is allowed.
* `WINDOWS_UPDATE_OTHER_MS_PRODUCTS`: Allows to update other Microsoft products via Windows Updates.
* `WINDOWS_UPDATE_CATEGORIES`: Windows Update categories to install.
* `WINDOWS_HOTFIXES`: List of Hotfixes in MSU format which are not installed via Windows Update
  but required for other programs to work.

Example
-------

```yaml
- hosts: win_servers
  vars:
    WINDOWS_UPDATE_OTHER_MS_PRODUCTS: true
    WINDOWS_UPDATE_CATEGORIES:
      - CriticalUpdates
      - SecurityUpdates
    WINDOWS_HOTFIXES:
      - { name: KB2999226, url: https://download.microsoft.com/download/D/1/3/D13E3150-3BB2-4B22-9D8A-47EE2D609FFF/Windows8.1-KB2999226-x64.msu }
      - { name: KB3035131, url: https://download.microsoft.com/download/B/2/4/B24FB08A-DEA8-4B4C-8EE4-B9F0FB180200/Windows8.1-KB3035131-x64.msu }

  roles:
    - role: valerius257.windows-updates
```
