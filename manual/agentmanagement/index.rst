.. _management_addagent:

================
Agent Management
================

On the OSSEC manager an agent is added with the `manage_agents` utility.
This utility is also used on the agent to add the authentication key,
allowing the agent to communicate with the manager.


`manage_agents` provides both a menu based interface and a command line
interface. When run without any arguments, the menu is presented.

If an agent is added with a specific IP address, it must be unique.
Duplicate IP addresses will cause issues with agents connecting to the server.


.. include:: add_agent.trst

.. include:: add_agent_example.trst

