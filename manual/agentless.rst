.. _manual_agentless:

====================
Agentless Management
====================

OSSEC has the capability to monitor systems which cannot accept an agent.
This is done via the `ossec-agentlessd` daemon for some checks, and syslog
for log monitoring.

agentlessd
^^^^^^^^^^

`ossec-agentlessd` performs active checks on devices that do not have OSSEC agents
installed on them.
These checks can include checking configurations for modification and running checksums
on files on the system.

Active agentless monitoring is disabled by default.
It can be enabled with the following command:

.. code-block:: console

   # /var/ossec/bin/ossec-control enable agentless

This does not start the process, only enables it.
It can be started manually by restarting the OSSEC processes:

.. code-block:: console

   # /var/ossec/bin/ossec-control restart

Or by starting the process manually:

.. code-block:: console

   # /var/ossec/bin/ossec-agentlessd


Adding Hosts
^^^^^^^^^^^^

Hosts can be added via the `register_host.sh` script.

The user, host, and password to access the host can be set with this script.


.. code-block:: console

   # /var/ossec/agentless/register_host.sh
   /var/ossec/agentless/register_host.sh options:
        add <user@host> [<passwd>] (<additional_pass>)
        list (passwords)

These hosts must also be defined in the `ossec.conf` to define which checks
are performed on them.

More information can be found in the `ossec.conf` configuration documentation.
The agentless_ section provides details.

The default checks bundled in OSSEC are:

.. code-block:: console

   main.exp
   ssh.exp
   ssh_asa-fwsmconfig_diff
   ssh_foundry_diff
   ssh_generic_diff
   ssh_integrity_check_bsd
   ssh_integrity_check_linux
   ssh_nopass.exp
   ssh_pixconfig_diff
   sshlogin.exp
   su.exp


.. _agentless: ../configuration/ossec_conf.html#agentless

