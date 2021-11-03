Lab 1 - Azure Network 101
#########################

.. image:: ../pictures/lab1/azure.png
   :width: 25pt
   :height: 25pt
   :align: right

To make things simple, we will use the F5 demo app (https://github.com/f5devcentral/f5-demo-httpd). This app will display the information we need to test MA (headers ...)

Azure Networking glossary
=========================

.. |subscription| image:: ../pictures/lab1/subscription.png
   :width: 20pt
   :height: 20pt
 
.. |rg| image:: ../pictures/lab1/rg.png
   :width: 20pt
   :height: 20pt
.. |vnet| image:: ../pictures/lab1/vnet.png
   :width: 20pt
   :height: 20pt
.. |subnet| image:: ../pictures/lab1/vnet.png
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




+----------------+-------------------------------------+----------------------------------------------------------------------------------------+
|      icon.     |              item.                  |                                   description                                          |
+================+=====================================+========================================================================================+
| |subscription| |           Subscription              | Within an Azure account (or tenant), Azure subscriptions are billing containers.       |
+----------------+-------------------------------------+----------------------------------------------------------------------------------------+
|                |              Region                 |Every resources in Azure are deployed in a geographical location                        |
|                |                                     |or Region (US-East, West-Europe...)                                                     |
|                |                                     |https://azure.microsoft.com/en-us/global-infrastructure/geographies/                    |
+----------------+-------------------------------------+----------------------------------------------------------------------------------------+
|                |        Availability Set (AS)        |A Region is composed of multiple Azure Datacenters ensuring geographic redundancy       |
|                |                                     |                                                                                        |
+----------------+-------------------------------------+----------------------------------------------------------------------------------------+
|      |rg|      |         Resource Group (RG)         |These are logical group to view and manage a set of resources (compute, storage,        |
|                |                                     |networking...) reflecting a sub-organization, a group of applications...                |
|                |                                     |Subscriptions can have multiple resource groups.                                        |
|                |                                     |An RG can span multiple regions however its metadata are stored in an admin specified   |
|                |                                     |region.                                                                                 |
+----------------+-------------------------------------+----------------------------------------------------------------------------------------+
|     |vnet|     |       Virtual Network (VNET)        |Within a Resource Group you can have one or multiple VNET. a VNET defines an IP address |
|                |                                     |range (ex. 10.10.0.0/16). Any resource within a VNET must fall within this address space|
|                |                                     |VNET can be connected together via **VNET peering** (same region) or.                   |
|                |                                     |**Global VNET Peering** across regions.                                                 |
+----------------+-------------------------------------+----------------------------------------------------------------------------------------+
|    |subnet|    |              Subnet                 |A VNET can contain one or multiple subnets within the specified address range           |
|                |                                     |(ex. subnet external - 10.10.100.0/24, subnet internal - 10.10.200.0/24,                |
|                |.                                    |management - 10.10.0.0/24)                                                              |
+----------------+-------------------------------------+----------------------------------------------------------------------------------------+
|      |vm|      |        Virtual Machine (VM)         |a VM or instance are defined by a VM family depending on its required amount of CPU and |
|                |                                     |RAM (B series, DS Series...), based on an image (private or from the market place) and  |
|                |                                     |one or multiple VNICs.                                                                  |
+----------------+-------------------------------------+----------------------------------------------------------------------------------------+
|     |vnic|     |   Virtual Network Interface (VNIC)  |In Azure, private and public IP addresses and DNS settings are not configured inside    |
|                |                                     |a VM but are set at the VNIC level. Each VNIC has one (primary) or multiple (secondary) |
|                |                                     |IP addresses within a subnet. IP addresses can be statically or dynamically assigned via|
|                |                                     |DHCP                                                                                    |
+----------------+-------------------------------------+----------------------------------------------------------------------------------------+
|     |nsg|      |     Network Security Group (NSG)    | Basic networking firewall rules that can be applied to a subnet or directly            |
|                |                                     | assigned to a VNIC.                                                                    |
+----------------+-------------------------------------+----------------------------------------------------------------------------------------+




Managing Azure resources
========================
There are multiple ways we can create, view, manage and delete Azure resources:
- Manually
   - Web Portal (https://portal.azure.com)
    .. image:: ../pictures/lab1/azure_portal.png
      :scale: 50%
      :align: center   
   - az cli (https://docs.microsoft.com/en-us/cli/azure/install-azure-cli)

- Automatically
   - from Cloud Templates: Azure Resource Manager (ARM) (https://docs.microsoft.com/en-us/azure/azure-resource-manager/templates/overview)
   - Infrastructure as code (https://registry.terraform.io/providers/hashicorp/azurerm/latest/docs)
   - Configuration Management (https://docs.microsoft.com/en-us/azure/developer/ansible/overview)
   




Azure Architectures
===================
Topology #1: Single VM accessible from Internet
-----------------------------------------------
**Description**:
this is a simple architecture where we have:
- a single Subscription (i.e. a billing entity in the Azure account)
- within this subscription we have a Resource Group called **myRG**
- within the **myRG** Resource Group, we have created a VNET called **myVNET** with an IP Address range of 10.10.0.0/16
- **myVNET** VNET has only a single subnet having an IP address space 10.10.0.0/24 included in the VNET IP Address space.
- On **mySubnet** we create a *vNIC* with an IP Address dynamically assigned on the 10.10.0.0/24
- In **myVNET** we deploy an Ubuntu **myVM** from the Azure Marketplace on a DS2_V3 instance type. **myVM** is associated with **myVNIC** network interface.
- We have two NSGs for network filtering:
  - at the subnet level where We allow all traffic from a known Public IP address (100.200.10.20/32)
  - at the NIC level where We have a more granular control and allow only HTTPS and SSH.


**Architecture**:
    .. image:: ../pictures/lab1/topology1.png
      :scale: 50%
      :align: center
      

**Terraform components**:
For your information, here is the corresponding terraform declaration. Please note the implicit references and dependencies between resources.


Topology #2: Hub & Spoke Architecture
-------------------------------------


Topology #3: Hybrid Cloud and site-to-site peering
--------------------------------------------------
