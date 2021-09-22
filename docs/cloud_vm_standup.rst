.. _cloud_vm_standup:

Standing up Compose Services in an Azure Cloud Virtual Machine
==============================================================

This page will walk you through the steps to set up a Microsoft Azure Virtual Machine 
(VM) for the purposes of deploying Gen3 Compose Services in the cloud.  This page 
assumes that the user has or can access the following resources:

Required Azure Resources
++++++++++++++++++++++++

* **Virtual Machine**

   * Microsoft Azure subscription

   * Azure Resource Group

   * Azure Virtual Network and Subnet

   * Recommended Configurations:

      * Size: Standard D2s v3

      * vCPUs: 2

      * RAM: 8 GiB

      * OS: Ubuntu Server 18.04 LTS

* **Azure Disk (OS HDD)**

   * Recommended Configuration: 64 GB size (default is 30 GB which is not enough space)

* **DNS Name/Record attached to Virtual Machine**

* **Public IP Address (of the Virtual Machine)**

Creating and Deploying an Azure Virtual Machine through the Azure Portal
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Create the Azure VM
-------------------

* Log in to http://portal.azure.com

* Click "Create a Resource"

* Find/Search for "Virtual Machine" and click "Create"

.. image:: images/cloud_vm_standup/azure_vm.png
   :width: 150
   :alt: Creating a Virtual Machine in Azure

* Select your Azure subscription and the resource group to be used

* Size dropdown -> select :code:`Standard_D2s_v3` which is $59.86/month

.. image:: images/cloud_vm_standup/standard_disk.png
   :width: 400
   :alt: Azure VM: Standard Size

* Choose 'password' for your authentication type and create a username and password

* Click 'Next: Disks' and then for OS disk type select 'Standard HDD'

* Click 'Next: Networking'

   * Select your preconfigured Virtual Network and Subnet

   * Ensure that no ports are open to the internet

* Click 'Review and Create' and validate your configuration, then click 'create'

Configure Networking
--------------------

* Choose 'Networking' from the left-hand toolbar

* Add 3 inbound port rules (PORTS 22, 80, 443) for your IP address and anyone else who wants to access the commons.

   * **Source**: IP Addresses
   * **Source IP**: Enter your IP address and any others for individuals who want to access the commons
   * **Source port ranges**: *
   * **Destination**: Any 
   * **Action**: Allow

* Choose 'Overview' from the left-hand toolbar

   * In the top section you will see 'DNS name: Not configured'
   * Click on 'Not Configured' and then create a DNS name (Azure will default to \*.eastus.cloudapp.azure.com)


Configuring Google OAuth Client ID for Fence
++++++++++++++++++++++++++++++++++++++++++++

Note that in a previous page of this guide (:ref:`compose_services_standup:Setting up Google OAuth Client ID for Fence`) we walked through how to configure 
Google OAuth for Fence.  On a cloud VM it is similar, except you will replace 
:code:`localhost` with your VM DNS name.

.. image:: images/cloud_vm_standup/google_oauth.png
   :width: 400
   :alt: Google OAuth Dialogue Box

Connecting to your VM through SSH
+++++++++++++++++++++++++++++++++

This guide recommends using Microsft VS Code Remote Explorer to connect to the VM 
that you created.  You will be connecting via SSH (Secure Shell).

* Open VS Code and install the Remote Explorer extension if not installed
* Open the Remote Explorer Extension along the left-hand pane

.. image:: images/cloud_vm_standup/remote_explorer.png
   :width: 100
   :alt: Remote Explorer icon 

* Add a new configuration for your VM's public IP address:
   * Host <your VM's public IP address>
   * HostName <your VM's public IP address>
   * User <your username from previous step>

* Connect to your VM by right-clicking the new connection and selecting either of the options (Note: you may need to click the refresh button to see new configurations that you've created)

Setting up Compose Services on the VM
+++++++++++++++++++++++++++++++++++++

The steps in this section will go over how to set up Gen3 Compose Services now that you 
have access to your newly-created VM.

* Install Docker and Docker Compose
   * Follow `this guide <https://docs.docker.com/engine/install/ubuntu/#installation-methods>`__ for Ubuntu.  It is recommended that you use the 'install using the repository' method.
   * Follow `this guide <https://docs.docker.com/compose/install/#install-compose-on-linux-systems>`__ for Docker-Compose help.

* Create a new directory to work in using the terminal or file explorer
* Open a terminal and route to your new directory (Terminal -> New Terminal in VS Code Toolbar)
* Run the following code to clone :code:`compose-services` and set up your credentials using the DNS name attached to your VM

.. code-block:: sh

    git clone https://github.com/uc-cdis/compose-services.git
    cd compose-services
    bash creds_setup.sh YOUR_CUSTOM_DOMAIN # Use the DNS set up in the previous steps

* Configure :code:`fence.yaml` using steps from :ref:`compose_services_standup:Configure fence-config.yaml`
* Refer to :ref:`compose_services_standup:Starting up your Local Gen3 compose-services Deployment` to start the commons
* Finally, go to your Data Commons at your registered DNS name.