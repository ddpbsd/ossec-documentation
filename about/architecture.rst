.. _about_architecture:

OSSEC Architecture
==================

On Microsoft Windows systems, OSSEC runs as a single service. On unix-like systems it runs as several
processes, communicating via sockets.


+--------------------+--------------------------------------------------------------------------------+
| Process            | Description                                                                    |
+====================+================================================================================+
| ossec-analysisd    | Master program. Analyzes data from the logs, syscheck,rootcheck, etc.          |
|                    | Runs as an unprivileged (ossec) user under chroot.                             |
+--------------------+--------------------------------------------------------------------------------+
| ossec-execd        | Execute active responses by calling the configured scripts. Runs as root.      |
+--------------------+--------------------------------------------------------------------------------+
| ossec-maild        | Send e-mail alerts. Runs as an unprivileged user (ossecm) under chroot.        |
+--------------------+--------------------------------------------------------------------------------+
| ossec-remoted      | Server side socket for server/client communications.                           |
|                    | Runs as an unprivileged user (ossecr) under chroot.                            |
+--------------------+--------------------------------------------------------------------------------+
| ossec-agentd       | Agent side socket for server/client communications.                            |
|                    | Runs as an unprivileged user (ossec) under chroot.                             |
+--------------------+--------------------------------------------------------------------------------+
| ossec-logcollector | Monitor log files and windows event logs (do not use tail).                    |
+--------------------+--------------------------------------------------------------------------------+
| ossec-syscheckd    | Does integrity checking and rootkit detection (rootcheck is a module of it).   |
+--------------------+--------------------------------------------------------------------------------+
| ossec-csyslogd     | Client syslog tool to forward OSSEC alerts to remote syslog servers            |
|                    | (including SIM/SEMs and log management systems).                               |
+--------------------+--------------------------------------------------------------------------------+
| ossec-monitord     | Monitor agent connectivity and compress daily log files.                       |
+--------------------+--------------------------------------------------------------------------------+

