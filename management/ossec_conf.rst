.. _management_ossec_conf:

==========
ossec.conf
==========

The configuration for OSSEC is mostly held in `/var/ossec/etc/ossec.conf`.


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

rootcheck:
----------

localfile:
----------

rules:
------

command:
--------

active-response:
----------------

alerts:
-------

Settings related to alert logging and notifications.

The `<alerts>` section is valid on Server and Local installations only.

.. include:: alerts.trst


email_alerts:
-------------

syslog_output:
--------------

database_output:
----------------

agentless:
----------

reports:
--------




