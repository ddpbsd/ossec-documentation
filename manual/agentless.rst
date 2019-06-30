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




.. code-block:: console

   # /var/ossec/agentless/register_host.sh
   /var/ossec/agentless/register_host.sh options:
        add <user@host> [<passwd>] (<additional_pass>)
        list (passwords)

