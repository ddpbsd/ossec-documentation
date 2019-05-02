.. _installation_build-options:

Build Options:
==============

OSSEC has a number of options that can be set or changed at build time.
These options can change the behavior or resource utilization by the OSSEC processes.


TARGET:
^^^^^^^

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

Optional:
^^^^^^^^^

A number of options are set in the `Makefile`, but can be modified at compile time.

**Available options:**

   - **ZLIB_SYSTEM:** If set to `yes` the system installed zlib will be used

   - **PCRE2_SYSTEM:** If set to `yes` the system installed pcre2 will be used

   - **LUA_ENABLE:** Enable building lua

   - **MAXAGENTS:** The maximum number of supported agents

   - **USE_PRELUDE:** Enable forwarding alerts to Prelude-IDS

   - **USE_ZEROMQ:** Enable forwarding events via ZeroMQ

   - **USE_GEOIP:** Enable Lookups against the GeoIP database

   - **USE_INOTIFY:** Enable realtime support in `syscheck` via `inotify` in Linux

   - **USE_PCRE2_JIT:** Enable the use of pcre2 JIT, must be supported by the installed pcre2

   - **REUSE_ID:** XXX 

Settings:
^^^^^^^^^


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

