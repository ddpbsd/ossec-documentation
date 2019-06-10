.. _manual_logmonitoring:

Log Monitoring
==============

What is log monitoring:
^^^^^^^^^^^^^^^^^^^^^^^

OSSEC can monitor log messages in real-time, comparing them to a set of pre-defined rules.
These rules can trigger alerts to notify analysts or administrators of a possible issue to be investigated.

These log messages can currently come from log files on the system or commands run by OSSEC.


log files:
^^^^^^^^^^

OSSEC can monitor text based log files from syslog on unix and Linux systems, and `EventLog` or `EventChannel` log formats on Windows based systems.

The `localfile` option can be used to monitor a log file. See the syntax for :ref:`syntax_localfile`.

commands:
^^^^^^^^^


