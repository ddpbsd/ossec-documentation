.. _management_agent_conf:

==========
agent.conf
==========

The file `/var/ossec/etc/shared/agent.conf` can be used for centralized configuration.
The `agent.conf` file (and the contents of `/var/ossec/etc/shared`) will be pushed from the OSSEC server to the agents.

.. note::

   The server itself does not read the configuration in the `agent.conf`.
   This file is only for use by the agents.

Many of the configuration options in the `ossec.conf` can be placed in teh agent.conf.
If the `agent.conf` is modified, the agent will have to be restarted for the changes to take effect.

Minimal ossec.conf:
^^^^^^^^^^^^^^^^^^^

At a minimum, the `<client>` section is necessary.
Without this, the agent does not know how to communicate with the server.

Minimal `ossec.conf` example:

.. code-block:: xml

   <ossec_config>
     <client>
     <server-hostname>ossec.example.com</server-hostname>
   </client>

Settings that will not work:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

By default the OSSEC agent will not run commands from an `agent.conf`.
Any `<localfile>` options that require `command` or `full_command` should be configured in the agent's `ossec.conf.`

