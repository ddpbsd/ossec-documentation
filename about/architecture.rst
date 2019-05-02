.. _about_architecture:

OSSEC Architecture
==================

Linux and unix-like systems:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

OSSEC runs as multiple processes, the exact number differing between agent, server, and local installations.
Most processes communicates through unix sockets under the `queue` directory inside of the OSSEC installation location.
When possible the OSSEC processes run with limited privileges and chroot to the install location.
This is modeled after the `Privilege Separation tehniques <https://www.openbsd.org/papers/auug04/mgp00030.html>`_ used in OpenBSD.

Windows:
^^^^^^^^

OSSEC runs as a single service.

Agent/Server Communication:
^^^^^^^^^^^^^^^^^^^^^^^^^^^

The OSSEC server listens on 1514/udp via `ossec-remoted`.
Agents send messages to the server via `ossec-agentd`.
The communication is two-way, but initiated by the agent.

Agentless and Network Devices:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

OSSEC has the ability to communicate with systems that cannot have the agent software installed.
This is typically done through SSH, and a few pre-made `Expect <https://core.tcl.tk/expect/index>`_
scripts are provided for a number of systems.

In addition to the agentless support, OSSEC can receive syslog messages from any number of devices and process them as if the
messages were delivered via an agent.

User List:
^^^^^^^^^^

+--------+---------------------------------------------------+
| User   | Process                                           |
+========+===================================================+
| root   | ossec-syscheckd, ossec-execd, ossec-logcollector  |
+--------+---------------------------------------------------+
| ossec  | ossec-analysisd, ossec-monitord, ossec-agentlessd |
+--------+---------------------------------------------------+
| ossecr | ossec-remoted                                     |
+--------+---------------------------------------------------+
| ossecm | ossec-maild, ossec-csyslogd                       |
+--------+---------------------------------------------------+

Process List:
^^^^^^^^^^^^^

+--------------------+--------------------------------------------------------------------------------+---------------------+
| Process            | Description                                                                    | Install Type        |
+====================+================================================================================+=====================+
| ossec-analysisd    | Master program. Analyzes data from the logs, syscheck, rootcheck, etc.         | Server/Stand-alone  |
|                    | Runs as an unprivileged (ossec) user under chroot.                             |                     | 
+--------------------+--------------------------------------------------------------------------------+---------------------+
| ossec-execd        | Execute active responses by calling the configured scripts. Runs as root.      | All                 |
+--------------------+--------------------------------------------------------------------------------+---------------------+
| ossec-maild        | Send e-mail alerts. Runs as an unprivileged user (ossecm) under chroot.        | Server/Stand-alone  |
+--------------------+--------------------------------------------------------------------------------+---------------------+
| ossec-remoted      | Server side socket for server/client communications.                           | Server              |
|                    | Runs as an unprivileged user (ossecr) under chroot.                            |                     |
+--------------------+--------------------------------------------------------------------------------+---------------------+
| ossec-agentd       | Agent side socket for server/client communications.                            | Agent               |
|                    | Runs as an unprivileged user (ossec) under chroot.                             |                     |
+--------------------+--------------------------------------------------------------------------------+---------------------+
| ossec-logcollector | Monitor log files and windows event logs (do not use tail).                    | All                 |
+--------------------+--------------------------------------------------------------------------------+---------------------+
| ossec-syscheckd    | Does integrity checking and rootkit detection (rootcheck is a module of it).   | All                 |
+--------------------+--------------------------------------------------------------------------------+---------------------+
| ossec-csyslogd     | Client syslog tool to forward OSSEC alerts to remote syslog servers            | Server/Stand-alone  |
|                    | (including SIEM and log management systems).                                   |                     |
+--------------------+--------------------------------------------------------------------------------+---------------------+
| ossec-monitord     | Monitor agent connectivity and compress daily log files.                       | Server/Stand-alone  |
+--------------------+--------------------------------------------------------------------------------+---------------------+

