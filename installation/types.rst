.. _installation_types:

Installation Types
==================

OSSEC can be installed in an agent/server combination or as a stand-alone system.
The stand-alone installation is essentially a server installation without the pieces that interact with agents.
The server installation includes the agent functionality for the local system.


Server:
^^^^^^^

Most of the processing is done on the OSSEC server, and the rules/decoders are installed there.

Agent:
^^^^^^

OSSEC agents tail the local log files and forward the messages to the OSSEC server.
Local file integrity monitoring messages are also forwarded to the server.

