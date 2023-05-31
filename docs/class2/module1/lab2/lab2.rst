Lab 2 - Allow HTTP Methods, File Types and Geolocalisation
##########################################################

.. note:: Positive Security is done via Service Policy. It is a another object/policy, separated from the WAAP policy

In this lab, we will create a Service Policy with 3 rules:

* Allow only GET and POST HTTP Methods
* Disallow some file types (exe, bat ...)
* Geoloc - disallow some countries


Create an New Service Policy and new rules as below

Disallow file types
*******************

* In your Service Policy, create a new rule
* Name it as you want ``file-type-deny``
* In action, set ``Deny``
* In Request Match, and HTTP Path, click ``configure``
* Add this value in the ``Regex Values``

  .. code-block:: BASH

      (.doc|.docx|.pdf|.exe|.bat)$

.. note:: This will disallow doc, docx, pdf, exe and bat file types.

|

Allow HTTP Methods
******************

* In the same Service Policy created, create a new rule
* Name it as you want ``method-allow``
* In action, set ``Allow``
* In Request Match, Configure ``HTTP Method``
* Add ``GET`` and ``POST``
* Save your rule.
* You should see now 2 rules

  * IP-Reputation rule
  * Methods allowed rule

|

.. note:: You should have 2 rules in your Service Policy. Check the order.

  .. image:: ../pictures/lab2/all-rules.png
     :align: center

|

Geoloc - disallow countries
***************************

* For Geolocalization or any Source IP rules, a ``new Service Policy`` is required. This can't be added to the L7 Custom Policy
* Create a new Service Policy named ``sp-geo``
* In the rules, instead of creating a custom rule, we wil create a ``Denied Sources`` rule
* In ``Country List``, select the countries you want to deny
* Check default action is set to ``Next Policy``

  .. image:: ../pictures/lab2/geo.png
     :align: center
     :scale: 50%

|



Assign your Service Policies to your HTTP LB
********************************************

* Now you can assign your 2 SP to your HTTP LB. The HTTP LB you prefer to make your test.
* Don't forget the order

  * First : SP Geoloc
  * Second : SP Positive Security

.. image:: ../pictures/lab2/apply-sp.png
   :align: center
   :scale: 50%

|

.. note:: Test your Service Policies :)

    