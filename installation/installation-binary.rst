.. _installation_installation-binary:

Compiling OSSEC for a Binary Installation 
=========================================

.. warning::

   This installation method should be revisited, it may not work.

In the past OSSEC was often compiled on each system it was installed on. This is not the only 
method of installation however. OSSEC can be compiled on one system and copied to a destination
system. This method of installation still requires GNU make on the target system, but not the 
compilers or development packages.

.. note:: 

    OSSEC has very limited cross compiling facilities. Windows binaries can be built on Linux systems, 
    but binaries for other systems should be built on a system of the same OS and CPU platform.

.. _manual-install-binary-build: 

Compiling OSSEC for install on a second server:
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

First download the OSSEC package corresponding to the version you want to 
install and extract it on the build system.

Enter in the source directory of the downloaded package, and configure OSSEC to build the ``agent`` version.
The ``make`` commands should compile the correct binaries.

.. code-block:: console 

    $ cd ossec-hids-*/src
    $ make TARGET=agent

Modify `ossec-hids-*/etc/preloaded-vars.conf` to set `BINARY_INSTALL` to yes. 

.. code-block:: console 

    $ echo "USER_BINARYINSTALL=\"y\"" >> ossec-hids*/etc/preloaded-vars.conf

Finally create an OSSEC package.

.. code-block:: console 

    $ tar -cvf ossec-binary.tar ossec-hids*

.. _manual-install-binary-install: 

Installation of the binary OSSEC package 
----------------------------------------

On the target system (that does not have a C compiler) download your ossec-binary.tar 
created in the steps above. 

Complete the installation by unarchiving the binary package and running `sudo ./install.sh`. 

.. code-block:: console 

    $ tar xfv ossec-binary.tar
    $ cd ossec-* 
    $ sudo ./install.sh 

After following the installation prompts the install will be complete.  

