.. _management_ossec_conf:

==========
ossec.conf
==========

The configuration for OSSEC is mostly held in `ossec.conf`.
It is written in loose XML, and consists of a number of sections.

.. _syntax_global:

global:
-------

The `<global>` section is valid on Server and Local installations only.

.. include:: global.trst

.. _syntax_client:

client:
-------

Settings defining how an OSSEC agent interacts with the OSSEC management server.
The `<client>` section is valid on Agents only.

.. include:: client.trst

.. _syntax_remote:

remote:
-------

Settings defining the configuration of `ossec-remoted` on the OSSEC management server.

.. include:: remote.trst

.. _syntax_syscheck:

syscheck:
---------

Settings controlling the file integrity monitoring features in OSSEC.
Most settings should be configured on the system they apply to, but
settings that are only valid on the management server or local installs
have been marked as such.

.. include:: syscheck.trst

.. _syntax_rootcheck:

rootcheck:
----------

Settings controlling the rootcheck functionality in OSSEC.

.. include:: rootcheck.trst

.. _syntax_localfile:

localfile:
----------

Settings specifying the location and format of logs for ingestion.

.. include:: localfile.trst

.. _syntax_rules:

rules:
------

Settings specifying rule locations.
These settings are only valid on a Server or Local installation.

.. include:: rules.trst

.. _syntax_command:

command:
--------

Definitions for commands available to the active response system.

.. include:: command.trst

.. _syntax_active-response:

active-response:
----------------


.. include:: active-response.trst

.. _syntax_alerts:

alerts:
-------

Settings related to alert logging and notifications.

The `<alerts>` section is valid on Server and Local installations only.

.. include:: alerts.trst

.. _syntax_email_alerts:

email_alerts:
-------------

Settings for which alerts should trigger emails.

.. include:: email_alerts.trst

.. _syntax_syslog_output:

syslog_output:
--------------

OSSEC is able to forward alerts via syslog in a number of formats.
These options are for use on a Server or Local installation.

.. include:: syslog_output.trst

.. _syntax_database_output:

database_output:
----------------

OSSEC can store alerts in MySQL or PostgreSQL databases.
These options are for use on a Server or Local installation.

.. note::

   OSSEC must be compiled with database support for `ossec-dbd` to function.

.. include:: database_output.trst

.. _syntax_agentless:

agentless:
----------

Configures scripts to be run against systems where an agent cannot be installed.

.. include:: agentless.trst

.. _syntax_reports:

reports:
--------

Configuration for automated daily reports.
This is only valid on Server and Local installations.

.. include:: reports.trst


