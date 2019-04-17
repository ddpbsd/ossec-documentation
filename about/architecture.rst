.. _about_architecture:

OSSEC Architecture
==================

OSSEC is comprised of multiplepieces that work together. In an agent/server configuration the central manager is responsible
for receiving information from agents, syslog devices, and from agentless devices.

In a stand-alone environment a system mostly monitors itself, performing all of the functions of both the agent and server.


Internal Architecture:
^^^^^^^^^^^^^^^^^^^^^^

On Microsoft Windows systems, OSSEC runs as a single service. On unix-like systems it runs as several
processes, communicating via sockets.

On an agent `ossec-agentd` communicated with the manager. It passes along messages from `ossec-syscheckd` and
`ossec-logcollector`.

On the OSSEC manager the `ossec-remoted` process is responsible for communicating with the agents, and passing the information
to `ossec-analysisd`. `ossec-analysisd` receives log messages and decodes them. It then compares the messages to a set of rules
and will iniate alerting when necessary.

Daemons like `ossec-maild` and `ossec-csyslogd` can read the alert log file and forward the alerts.

.. Insert picture of data flow through OSSEC


Agentless and Network Devices:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

OSSEC has the ability to communicate with systems that cannot have the agent software installed. This is typically done through
SSH, and a few pre-made `Expect <https://core.tcl.tk/expect/index>`_ scripts are provided for a number of systems.

In addition to the agentless support, OSSEC can receive syslog messages from any number of devices and process them as if the
messages were delivered via an agent.


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

