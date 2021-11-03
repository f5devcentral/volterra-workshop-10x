Lab 1 - Azure Network 101
#########################

 .. image:: ../pictures/lab1/Azure.png
   :scale: 20%
   :align: right

To make things simple, we will use the F5 demo app (https://github.com/f5devcentral/f5-demo-httpd). This app will display the information we need to test MA (headers ...)

Azure Networking glossary
=========================

.. |subscription| image:: ../pictures/lab1/subscription.png
   :width: 20pt
   :height: 20pt
.. |region| image:: ../pictures/lab1/subscription.png
   :width: 20pt
   :height: 20pt
.. |as| image:: ../pictures/lab1/subscription.png
   :width: 20pt
   :height: 20pt
.. |rg| image:: ../pictures/lab1/subscription.png
   :width: 20pt
   :height: 20pt
.. |vnet| image:: ../pictures/lab1/vnet.png
   :width: 20pt
   :height: 20pt
.. |subnet| image:: ../pictures/lab1/subscription.png
   :width: 20pt
   :height: 20pt
.. |vm| image:: ../pictures/lab1/vm.png
   :width: 20pt
   :height: 20pt
.. |vnic| image:: ../pictures/lab1/vnic.png
   :width: 20pt
   :height: 20pt
.. |nsg| image:: ../pictures/lab1/nsg.png
   :width: 20pt
   :height: 20pt




+----------------+-------------------+----------------------------------------------------------------------------------------------------------+
|      icon.     +       item.        +                                   description                                                           |
+================+===================+==========================================================================================================+
| |subscription| +     Subscription   +  Within an Azure account (or tenant), Azure subscriptions are billing containers.                       |
+----------------+-------------------+----------------------------------------------------------------------------------------------------------+
|    |region|.   +       Region.        +  Every resources in Azure are deployed in a geographical location or Region (US-East, West-Europe...) |
+----------------+-------------------+----------------------------------------------------------------------------------------------------------+
|      |as|      +   Availability Set (AS)   +  A Region is composed of multiple Azure Datacenters ensuring geographic redundancy               |
+----------------+-------------------+----------------------------------------------------------------------------------------------------------+
|      |rg|      +   Resource Group (RG)   +  Within an Azure account (or tenant), Azure subscriptions are billing containers.                  |
+----------------+-------------------+----------------------------------------------------------------------------------------------------------+
|     |vnet|     +   Virtual Network (VNET)   +  Within an Azure account (or tenant), Azure subscriptions are billing containers.               |
+----------------+-------------------+----------------------------------------------------------------------------------------------------------+
|    |subnet|    +   Subnet          +  A VNET contains multiple subnets within the specified address range (ex. subnet external - 10.10.100.0/24, subnet internal - 10.10.200.0/24, management - 10.10.0.0/24)                  |
+----------------+-------------------+----------------------------------------------------------------------------------------------------------+
|      |vm|      +   Virtual Machine (VM)   +  Within an Azure account (or tenant), Azure subscriptions are billing containers. |
+----------------+-------------------+----------------------------------------------------------------------------------------------------------+
|     |vnic|     +   Virtual Network Interface (VNIC)  +  Within an Azure account (or tenant), Azure subscriptions are billing containers. |
+----------------+-------------------+----------------------------------------------------------------------------------------------------------+
|      |nsg|     +   Network Security Group (NSG)   +  Within an Azure account (or tenant), Azure subscriptions are billing containers. |
+----------------+-------------------+----------------------------------------------------------------------------------------------------------+





https://azure.microsoft.com/en-us/global-infrastructure/geographies/











Pre-requisites:
portal.azure.com

az cli
installation
how to us it?

Azure Architectures
===================
Topology #1: Single VM accessible from Internet
-----------------------------------------------
Description:

Architecture:

Componnents:

Terraform components:


Topology #2: Hub & Spoke Architecture
-------------------------------------


Topology #3: Hybrid Cloud and site-to-site peering
--------------------------------------------------
