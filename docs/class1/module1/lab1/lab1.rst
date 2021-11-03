Architecture of the UDF lab
###########################

To make things simple, we will use the F5 demo app (https://github.com/f5devcentral/f5-demo-httpd). This app will display the information we need to test MA (headers ...)

**Architecture in place**

In UDF, we will use:

* 1 x MA instance
* 1 x Jumphost linux instance
* 1 x Windows 2019 server (jumphost and AD server)

.. image:: ../pictures/lab1/lab-archi.png
   :align: center

|

**Use cases to be tested on October 2021**

MA is under development. In October, we will validate and test 5 use cases:

#. SAML SP authentication with Azure AD as IDP (manual config)
#. SAML SP authentication with Azure AD as IDP (metadata config)
#. SAML SP auth + HTTP header insertion SSO
#. SAML SP auth + Kerberos Constrained Delegation SSO
#. SAML SP authentication with Azure AD as IDP via AS3 declaration (similar to Use Case #1 but via AS3)


.. note:: As you can imagine, new use cases will come over next quarters and we will run new Bugbash to validate them.