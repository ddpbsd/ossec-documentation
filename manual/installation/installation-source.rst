.. _installation_install-source:

===================
Install from source
===================

For source installations the `install.sh` script will ask questions about the installation,
compile, and install the necessary files and users.

Please check the :ref:`installation_installation-requirements` to ensure everything necessary is installed.
This document will assume the installation requirements are met.


Manager/Agent Installation
^^^^^^^^^^^^^^^^^^^^^^^^^^

1. Download the latest version and verify its checksum.

2. Extract the compressed OSSEC tarball. and run the ``install.sh`` script. It will guide you 
   through the installation and compile the source (not shown).

    .. code-block:: console 

        $ tar -zxvf ossec-hids-*.tar.gz (or gunzip -d; tar -xvf)
        $ cd ossec-hids-* 
        $ sudo ./install.sh

3. The OSSEC manager listens on UDP port 1514. All firewalls between the agents and 
   the manager will need to allow this traffic.

4. Start OSSEC HIDS by running the following command:

    .. code-block:: console 

        $ sudo /var/ossec/bin/ossec-control start  


Manual Installation:
^^^^^^^^^^^^^^^^^^^^

OSSEC can also be installed in a more manual fashion without the use of `install.sh`.
This installation method requires manual configuration of the `ossec.conf` file.
The `ossec`, `ossecm`, and `ossecr` users will still be created automatically.

After the source tarball is downloaded and extracted:

.. code-block:: console

   $ cd ossec-hids-*/src
   $ make TARGET=<server|local|agent>
   $ sudo make install

Build options can still be passed to `make` (`USE_ZEROMQ`, `USE_GEOIP`, etc.).

