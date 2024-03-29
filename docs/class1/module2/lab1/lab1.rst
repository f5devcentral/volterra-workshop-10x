Lab 1 - Expose the private Arcadia application
##############################################

Create the networking objects
*****************************

For this lab, we will use the following object naming convention

.. table:: Naming Convention
   :widths: auto

   ===============    ===========================================================================================
   Object               Value
   ===============    ===========================================================================================
   HTTP LB              **EMEA-SE** tenant : https://arcadia-re-ce-<se_name>.emea-ent.f5demos.com
                        
                        **F5-EMEA-WORKSHOP** tenant : https://arcadia-re-ce-<student_name>.workshop.emea.f5se.com

                        **F5-CHANNEL** tenant : https://arcadia-re-ce-<partner-name>.f5-channel.f5demos.com

                        Enable HTTPS AutoCert

   Origin Pool          Select ``IP Address of OP on Given site``

                        IP ``172.21.2.4``
   
                        Site for **EMEA-SE tenant** ``demo-waap-emea``

                        Site for **F5-EMEA-WORKSHOP tenant** ``emea-azure-node``

                        Site for **F5-CHANNEL tenant** ``azure-emea-waap``
   
                        Select ``Inside Network``

                        Port 80

                        NO TLS
   ===============    ===========================================================================================

* Check you are in your Namespace
* Create the Origin Pool targeting Arcadia private IP on given site

  .. image:: ../pictures/lab1/OP.png
     :align: center

* Create the HTTPS LB
* Assigned the  WAAP policy created in previous LAB



|

Test your Anycast HTTPS LB
**************************

* Check your Arcadia application is exposed and reachable from the F5XC Global Network
* Send Attacks as previous lab

|

.. note:: In this lab, you created a Multi-Cloud architecture where the application resides in a private location. And SecOps don't have to know where is the app and how to reach this app. NetOps created the relevant Network Infrastrucute (Mesh Node) and SecOps just consume the objects created by NetOps.