ansible-redhat-access-insights-client
========

Ansible role that installs, configures, and registers to the Red Hat Access Insights Service

Requirements
------------

N/A

Role Variables
--------------

N/A

Dependencies
------------

N/A

Example Playbook
-------------------------

You will want to import this role conditionally, perhaps as such:

    - hosts: all
      roles:
      - { role: redhataccess.redhat-access-insights-client, when: ansible_os_family == 'RedHat' }


License
-------

MIT

Author Information
------------------

Dan Varga <dvarga@redhat.com>
