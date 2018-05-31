redhat-access-insights-client
========

Installs, configures, and registers a system to the [Red Hat Insights service](http://access.redhat.com/insights).  This role is intended to work on RHEL 6 or RHEL 7, though it will generally work on any yum based system that has access to the redhat-access-insights RPM.

Requirements
------------

N/A

Role Variables
--------------
These are the available variables and their default settings:

Change log level, valid options DEBUG, INFO, WARNING, ERROR, CRITICAL. Default DEBUG

    loglevel: DEBUG

Attempt to auto configure with Satellite server

    auto_config: True

Change authentication method, valid options BASIC, CERT. Default BASIC

    authmethod: BASIC

Username to use when authmethod is BASIC

    username: ""

Password to use when authmethod is BASIC

    password: ""

URL of Insights API

    base_url: "cert-api.access.redhat.com:443/r/insights"

URL for your proxy.  Example: http://user:pass@192.168.100.50:8080

    proxy: ""

Location of the certificate chain for api.access.redhat.com used for Certificate Pinning.  
Valid options are True, False, or a path to the pinned certificate(s).

    cert_verify: "/etc/redhat-access-insights/cert-api.access.redhat.com.pem"

Enable/Disable GPG verification of dynamic configuration

    gpg: True

Automatically update the dynamic configuration

    auto_update: True

Obfuscate IP addresses

    obfuscate: False

Obfuscate hostname

    obfuscate_hostname: False

Log each line executed

    trace: False

Disallow Insights from creating cron job

    no_schedule: False

Replace the existing insights-client.conf with template version

    replace_config: yes

Force re-registration of agent

    force_register: False

Display name for registration

    insights_display_name: "{{ inventory_hostname_short }}"

Sets or resets the Display Name/System Name within Insights.  Insights needs an easily identifiable
name for each system.  If no explicit display name is given to a system, Insights uses it's hostname.
If a system's hostname is not easily identifiable, like "localhost" or "d4098731408", you can give
it a better name by setting 'insights_display_name'

If undefined (not set at all), this role will not make changes to a system's display name.

If defined (set) to be the empty string, this role will remove any previously set display name
for the system, and cause it to use the systems hostname as it's Display name/System name.

If defined to be a non-empty string, this role will replace any previously set display name
for the system with the given string.

Dependencies
------------

N/A

Example Playbook
----------------

    - hosts: all
      roles:
      - { role: redhataccess.redhat-access-insights-client, when: ansible_os_family == 'RedHat' }

If a system's hostname is not easily identifieable, but inventory_hostname is,
set insights_display_name set to be inventory_hostname:

    - hosts: all
      roles:
      - role: redhataccess.redhat-access-insights-client
        insights_display_name: "{{ inventory_hostname }}"
        when: ansible_os_family == 'RedHat'




Example Use
-----------

1. On a system where [Ansible is installed](http://docs.ansible.com/ansible/intro_installation.html), run the following command:

    ```bash
    $ ansible-galaxy install redhataccess.redhat-access-insights-client
    ```

1. Copy the Example Playbook to a file named 'install-insights.yml'.

1. Run the command, replacing 'myhost.example.com' with the name of the
   system where you want to install the insights client.

    ```bash
    $ ansible-playbook --limit=myhost.example.com install-insights.yml
    ```

License and Author
------------------

See GitHub source repo
