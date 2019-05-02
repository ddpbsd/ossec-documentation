

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
