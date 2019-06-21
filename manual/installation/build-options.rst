.. _installation_build-options:

=============
Build Options
=============

OSSEC has a number of options that can be set or changed at build time.
These options can change the behavior or resource utilization by the OSSEC processes.

Required
========

TARGET
^^^^^^

The `TARGET` is the type of system being built.

This is set during the compilation, either through the `install.sh` script or manually in the `src` directory:

.. code-block:: console

   $ cd ossec-hids-*/src
   $ make TARGET=server

**Available options:**

   - **server:** OSSEC Management Server

   - **local:** Local OSSEC installation

   - **agent:** OSSEC Agent

   - **hybrid:** Hybrid OSSEC server

   - **winagent:** Windows Agent

Optional
========

A number of options are set in the `Makefile`, but can be modified at compile time.

ZLIB_SYSTEM
^^^^^^^^^^^
   If set to `yes` the system installed zlib will be used

   *Default:* yes

PCRE2_SYSTEM
^^^^^^^^^^^^

   If set to `yes` the system installed pcre2 will be used

   *Default:* no

LUA_ENABLE
^^^^^^^^^^

   If set to `yes` the installation process will build lua

   *Default:* no

MAXAGENTS
^^^^^^^^^

   The maximum number of supported agents

   *Default:* 2048

USE_PRELUDE
^^^^^^^^^^^

   Enable forwarding alerts to Prelude-IDS

   *Default:* no

USE_ZEROMQ
^^^^^^^^^^

   Enable forwarding events via ZeroMQ

   *Default:* no

USE_GEOIP
^^^^^^^^^

   Enable Lookups against the GeoIP database

   *Default:* no

USE_INOTIFY
^^^^^^^^^^^

   Enable realtime support in `syscheck` via `inotify` in Linux

   *Default:* enabled on Linux and Windows, disabled on other operating systems

USE_PCRE2_JIT
^^^^^^^^^^^^^

   Enable the use of pcre2 Just In Time (JIT) support.
   If the installation process compiles PCRE2 this will be enabled.
   If the system installed PCRE2 is used, it must support JIT if this is enabled.

   *Default:* yes

REUSE_ID
^^^^^^^^

   Allow `authd` to re-use agent IDs

   *Default:* no

Settings
^^^^^^^^

A listing of the default settings.

.. code-block:: console

   $ cd ossec-hids-*/src
   $ make settings

   General settings:
       TARGET:           server
       V:
       DEBUG:
       DEBUGAD:
       PREFIX:           /var/ossec
       MAXAGENTS:        2048
       REUSE_ID:         no
       DATABASE:
       ONEWAY:           no
       CLEANFULL:        no
   User settings:
       OSSEC_GROUP:      ossec
       OSSEC_USER:       ossec
       OSSEC_USER_MAIL:  ossecm
       OSSEC_USER_REM:   ossecr
   ZLIB settings:
       ZLIB_SYSTEM:      yes
       ZLIB_INCLUDE:
       ZLIB_LIB:         os_zlib.a
   PCRE2 settings:
       PCRE2_SYSTEM:     y
       PCRE2_INCLUDE:
   Lua settings:
       LUA_PLAT:         posix
       LUA_ENABLE:       no
   USE settings:
       USE_ZEROMQ:       no
       USE_GEOIP:        no
       USE_PRELUDE:      no
       USE_OPENSSL:      auto
       USE_INOTIFY:      no
       USE_SQLITE:
       USE_PCRE2_JIT:    yes
   Mysql settings:
       includes:
       libs:
   Pgsql settings:
       includes:
       libs:
   Defines:
       -DMAX_AGENTS=2048 -DOSSECHIDS -DDEFAULTDIR="/var/ossec" -DUSER="ossec" -DREMUSER="ossecr" -DGROUPGLOBAL="ossec" -DMAILUSER="ossecm" -DOpenBSD -pthread -DZLIB_SYSTEM -DUSE_PCRE2_JIT -DLIBOPENSSL_ENABLED
   Compiler:
       CFLAGS          -I/usr/local/include -DMAX_AGENTS=2048 -DOSSECHIDS -DDEFAULTDIR="/var/ossec" -DUSER="ossec" -DREMUSER="ossecr" -DGROUPGLOBAL="ossec" -DMAILUSER="ossecm" -DOpenBSD -pthread -DZLIB_SYSTEM -DUSE_PCRE2_JIT -DLIBOPENSSL_ENABLED -Wall -Wextra -I./ -I./headers/
       LDFLAGS          -lm -L/usr/local/lib -lpcre2-8 -lssl -lcrypto -lz
       CC              cc
       MAKE            gmake

