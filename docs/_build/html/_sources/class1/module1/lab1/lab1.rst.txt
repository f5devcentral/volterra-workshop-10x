Architecture of the lab
#######################

The application used in the lab
*******************************

For this lab, we will use this application : http://sentence.emea.f5se.com

This application is a modern application displaying a sentence with 4 words. Each word comes from a word generator micro-service.

.. image:: ../pictures/lab1/lab1-app.png
   :align: center

|

The lab architecture
********************

As you can notice in the chart below, the Sentence application is running in our own datacenter, and is already available on internet (http://sentence.emea.f5se.com)
We will expose this application on the Volterra Global Network by configuring the following VoltConsole components:

* Origin Pool
* HTTP Load Balancer

Terminology
===========

**HTTP Load Balancer**
Volterra’s reverse proxy and HTTP load balancer concepts allow for flow control of application and API traffic between services, to the internet, and from clients on the internet. HTTP Load Balancers allow for steering decisions based on URI or other HTTP based criteria.

**Origin Pool**
An origin pool is a mechanism to configure a set of application endpoints grouped together into a resource pool. These endpoints could be IP:port tuples within a give site or a service discovered by one of Volterra’s many service discovery methods. These objects will be used the next step.

.. image:: ../pictures/lab1/lab1-archi.png
   :align: center



.. note:: The goal is to publish this application through the Volterra Global Network so people all over the world can reach the closest Votlerra RE.

 