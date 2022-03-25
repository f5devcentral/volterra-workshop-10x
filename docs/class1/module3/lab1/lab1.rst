Lab 1 - Expose the private Arcadia application through the Mesh Node only (CE-Only)
###################################################################################

For this lab, as the Mesh Node is shared between all SE/Students, we will use a ``fake FQDN/DNS for your LB``. There is one DNS provided by Azure, but so that all of SE/Students can push their own HTTP LB, each of you will use a fake FQDN for the LB. You will add a new entry in your ``Host file`` in order to target the Azure Mesh Node LB public IP addess.

FYI, the public Azure IP address of the node is:

* For **EMEA-SE tenant** ``20.224.0.208``
* For **F5-SALES-PUBLIC tenant** ``20.86.17.42``

Create a HTTP LB and expose it on the Mesh Node only
****************************************************

If you understand correctly this use case, we want the WAAP policy applied on a HTTP LB exposed on the Mesh Node in Azure only. We don't want the users/consumers to transit through the F5XC Global Network.

* Create a new ``HTTP LB`` - NOT A HTTPS LB.
* For the FQDN, use this convention ``arcadia-<se_name_or_student_id>-ceonly.fakefqdn.azure``
* Select the Origin Pool used and created in the previous lab. The private Origin Pool.
* Expose this LB on ``dierick-demowaap`` site

  * In VIP Configuration, enable ``Show Advanced Fields``
  * Advertise Custom
  * Create a new custom config (show advanced fields)
  * Select the ``dierick-demowaap`` site and expose on ``outside`` interface (the one exposed by the Azure LB)

  .. image:: ../pictures/lab1/custom-vip.png
     :align: center

* Assign your WAAP policy

Modify you Host file entries
****************************

* Modify your host file in order to target the right Azure IP address (look at above which address to use based on your Tenant) for the FQDN created ``arcadia-<se_name>-ceonly.fakefqdn.azure``


Test your CE-Only lab
*********************

* As previous labs, connect to your LB and send attacks

.. note:: As you can notice, in the 3 use cases, we keep consistancy with one WAAP policy whereever the LB or the App reside. 

