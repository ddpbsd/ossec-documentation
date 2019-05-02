.. _management_ossec_conf:

==========
ossec.conf
==========

The configuration for OSSEC is mostly held in `ossec.conf`.
It is written in loose XML, and consists of a number of sections.


global:
-------

The `<global>` section is valid on Server and Local installations only.

.. include:: global.trst

client:
-------

Settings defining how an OSSEC agent interacts with the OSSEC management server.
The `<client>` section is valid on Agents only.

.. include:: client.trst

remote:
-------

Settings defining the configuration of `ossec-remoted` on the OSSEC management server.

.. include:: remote.trst

syscheck:
---------

Settings controlling the file integrity monitoring features in OSSEC.
Most settings should be configured on the system they apply to, but
settings that are only valid on the management server or local installs
have been marked as such.

.. include:: syscheck.trst

rootcheck:
----------

Settings controlling the rootcheck functionality in OSSEC.

.. include:: rootcheck.trst

localfile:
----------

Settings specifying the location and format of logs for ingestion.

.. include:: localfile.trst

rules:
------

Settings specifying rule locations.
These settings are only valid on a Server or Local installation.

.. include:: rules.trst

command:
--------

Definitions for commands available to the active response system.

.. include:: command.trst

active-response:
----------------


.. include:: active-response.trst

alerts:
-------

Settings related to alert logging and notifications.

The `<alerts>` section is valid on Server and Local installations only.

.. include:: alerts.trst


email_alerts:
-------------

Settings for which alerts should trigger emails.

.. include:: email_alerts.trst

syslog_output:
--------------

OSSEC is able to forward alerts via syslog in a number of formats.
These options are for use on a Server or Local installation.

.. include:: syslog_output.trst

database_output:
----------------

OSSEC can store alerts in MySQL or PostgreSQL databases.
These options are for use on a Server or Local installation.

.. note::

   OSSEC must be compiled with database support for `ossec-dbd` to function.

.. include:: database_output.trst

agentless:
----------

Configures scripts to be run against systems where an agent cannot be installed.

.. include:: agentless.trst

reports:
--------

Configuration for automated daily reports.
This is only valid on Server and Local installations.

.. include:: reports.trst


