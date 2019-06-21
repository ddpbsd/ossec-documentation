.. _management_addagent:

================
Agent Management
================

On the OSSEC management server an agent can be added in multiple ways.
The first method is adding an agent with the `manage_agents` utility.
The second is using `ossec-authd`. This is a process on the ossec
management server that receives key requests, adds an agent,
and sends the key to the new agent.


manage_agents
^^^^^^^^^^^^^

The `manage_agents` utility is run on both the OSSEC management server
and the OSSEC agent.
On the management server it will add an agent and export a key to be
imported on the agent.
On the agent the `manage_agents` utility will import a key for authenticating the agent
to the management server.

`manage_agents` provides both a menu based interface and a command line
interface. When run without any arguments, the menu is presented.

If an agent is added with a specific IP address, it must be unique.
Duplicate IP addresses will cause issues with agents connecting to the server.


.. include:: add_agent.trst

.. include:: authd.trst

.. include:: add_agent_example.trst

.. include:: authd_example.trst

