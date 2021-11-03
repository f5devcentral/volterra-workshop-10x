Module 1 - BIG-IP MA
####################

In this section, we will deploy a BIG-IP MA (Modular Architecture) in order to test several use cases covered by BIG-IP MA APM in October 2021.

.. note:: The goal of a bugbash is to discover bugs, but also provide with feedbacks to the Produt Management. What's more, it is a great opportunity for the field to be part of new product development and integration.

.. note:: As of today, we will run all the configuration steps from API calls. There is a Local GUI we will test, but all settings will be sent from Postman. An of course, the full GUI will come with BIG-IP MA Central Manager.

|

**Use cases** covered:

#. SAML SP authentication with Azure AD as IDP (manual config)
#. SAML SP authentication with Azure AD as IDP (metadata config)
#. SAML SP auth + HTTP header insertion SSO
#. SAML SP auth + Kerberos Constrained Delegation SSO
#. SAML SP authentication with Azure AD as IDP via AS3 declaration (similar to Use Case #1 but via AS3)

--------------------

But before publishing your first application with BIG-IP MA, it is important to understand how to ``onboard`` the MA.

#. Onboard the MA
#. Define the networks
#. Understand the concept of ``stacks``

---------------------

**Known bugs** discovered during the creation of this bugbash:

* A policy (WAF or APM) can't be updated. It has to be DELETED and RE-CREATED
* DNS resolver in TMOS: the BIG-IP MA containers inherit from the host. In this lab, the host DNS file will be updated accordingly.
* If MA is shutted down, the configuration does not load. Application and policies have to be DELETED and RE-CREATED
* Every new BIG-IP MA onboarding will create a new entry in /etc/resolv.conf

  * Workaround: clean up the /etc/resolv.conf with only one entry (10.1.20.6) 

**Module 1 - All sections**

.. toctree::
   :maxdepth: 1
   :glob:

   lab*/lab*

