ansible-redhat-access-insights-client
========

Ansible role that installs, configures, and registers a system to the [Red Hat Insights service](http://access.redhat.com/insights).  This role is intended to work on RHEL 6 or RHEL 7, though it will generally work on any yum based system that has access to the redhat-access-insights RPM.

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
----------------

    - hosts: all
      roles:
      - { role: redhataccess.redhat-access-insights-client, when: ansible_os_family == 'RedHat' }


Example Use
-----------

1. On a system where [Ansible is installed](http://http://docs.ansible.com/ansible/intro_installation.html), run the following command:

    ansible-galaxy install redhataccess.redhat-access-insights-client

1. Copy the Example Playbook to a file named 'install-insights.yml'.

1. Run the command, replacing 'myhost.example.com' with the name of the
   system where you want to install the insights client.

    ansible-playbook --limit=myhost.example.com install-insights.yml


License
-------

MIT

Author Information
------------------

Dan Varga <dvarga@redhat.com>
