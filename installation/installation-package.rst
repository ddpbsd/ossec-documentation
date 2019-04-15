.. _installation_installation-package:


Package Installation
====================

The OSSEC project has made RPM and deb packages available.
Links to the packages can be found on the OSSEC `download page <http://www.ossec.net/?page_id=19>`_

RPM Installation:
^^^^^^^^^^^^^^^^^

OSSEC's RPMs are made available by `AtomiCorp <http://www.atomicorp.com>`_.

The RPMs can be installed by adding the AtomiCorp yum repository:

.. code-block:: console

   # wget -q -O - https://updates.atomicorp.com/installers/atomic | sh 

Next use ``yum`` to install the specific packages. For an OSSEC server run:

.. code-block:: console

   # yum install ossec-hids ossec-hids-server

And for an agent run:

.. code-block:: console

   # yum install ossec-hids ossec-hids-agent


Deb Installation:
^^^^^^^^^^^^^^^^^

Atomicorp provides `.deb` installation packages as well.

Install the apt-get repository key:

.. code-block:: console
    
    # wget -q -O - https://www.atomicorp.com/RPM-GPG-KEY.atomicorp.txt  | sudo apt-key add -

Add the repository for Debian and Ubuntu:

.. code-block:: console

    # wget -q -O - https://updates.atomicorp.com/installers/atomic | sudo bash

Update the repository:
 
.. code-block::console

    # apt-get update

Install OSSEC HIDS server/manager:

.. code-block:: console

    # apt-get install ossec-hids-server

Or install OSSEC HIDS agent:

.. code-block:: console

    # apt-get install ossec-hids-agent

FreeBSD Ports:
^^^^^^^^^^^^^^

*TBD*


