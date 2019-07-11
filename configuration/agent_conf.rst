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


Syntax
^^^^^^

Each block of configuration should be surrounded by `<agent_config>`.
There can be multiple `<agent_config>` blocks in the `agent.conf`.

.. code-block:: console

   <agent_config>

     <!-- Configuration goes here -->

   </agent_config>

Each block can be restricted with 3 options.
The options are `os` to limit by operating system, `name` to limit by the agent name, and `profile` to use agent profiles.
Every agent that matches the restriction will apply the configuration block.
Every agent will apply a configuration block that does not contain a restriction.

.. _agent_os:

os
^^

   The general operating system can be specified with `os`.
   Typical options include `Windows` and `Linux`.

   .. code-block:: xml

      <agent_config os="Windows">

name
^^^^

   .. XXX Link to manage_agents and authd

   An agent name can be specified with `name`.
   This is the name the agent is given when it is added with `manage_agents </manual/agentmanagement/index.html#manage-agents>`_ or `authd </manual/agentmanagement/index.html#ossec-authd>`_.

   .. code-block:: xml

      <agent_config name="agent007">

profile
^^^^^^^

   A `profile <./ossec_conf.html#config-profile>`_ is a group of similar agents that can agent can subscribe to in its `ossec.conf`.

   .. code-block:: xml

      <agent_config profile="webservers">


Minimal ossec.conf
^^^^^^^^^^^^^^^^^^

At a minimum, the `<client>` section is necessary.
Without this, the agent does not know how to communicate with the server.

Minimal `ossec.conf` example:

.. code-block:: xml

   <ossec_config>
     <client>
     <server-hostname>ossec.example.com</server-hostname>
   </client>

Settings that will not work
^^^^^^^^^^^^^^^^^^^^^^^^^^^

By default the OSSEC agent will not run commands from an `agent.conf`.
Any `<localfile>` options that require `command` or `full_command` should be configured in the agent's `ossec.conf.`

