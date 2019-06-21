.. _manual_logmonitoring:

==============
Log Monitoring
==============

What is log monitoring
^^^^^^^^^^^^^^^^^^^^^^

OSSEC can monitor log messages in real-time, comparing them to a set of pre-defined rules.
These rules can trigger alerts to notify analysts or administrators of a possible issue to be investigated.

These log messages can currently come from log files on the system, commands run by OSSEC on the system
and via syslog from networked devices.


log files
^^^^^^^^^

OSSEC can monitor text based log files from syslog on all systems,
and `EventLog` or `EventChannel` log formats on Windows based systems.

The `localfile` option can be used to monitor a log file.
See the syntax for :ref:`syntax_localfile` for more information.

commands
^^^^^^^^

OSSEC is able to run commands on a system and monitor the output.
The command will be run periodically, with a admin configurable frequency.
The command output can be monitored for content directly, or for changes between runs.


See the syntax for :ref:`syntax_command` for more information..

syslog
^^^^^^

OSSEC is able to receive syslog messages from systems that cannot have an agent installed on them.
This insludes many network devices like routers, firewalls, and switches.

See the :ref:`syntax_remote` documentation for more information.

