Lab 2 - Expose the public application
#####################################

Create the networking objects
*****************************

For this lab, we will use the following object naming convention

.. table:: Naming Convention
   :widths: auto

   ===============    ================================================
   Object               Value
   ===============    ================================================
   HTTP LB              https://arcadia-<se_name>.emea-ent.f5demos.com
                        
                        Enable HTTPS AutoCert

   Origin Pool          https://arcadia.emea.f5se.com

                        Disable TLS Verifiation
   ===============    ================================================

* Check you are in your Namespace
* Create the Origin Pool targeting Arcadia public app
* Create the HTTPS LB

|

Test your Anycast HTTPS LB
**************************

* Check your Arcadia application is exposed and reachable from the F5XC Global Network

.. note:: So far, Arcadia is not protected but exposed all over the world on all F5XC RE.