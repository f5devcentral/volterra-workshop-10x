Lab 3 - Deploy Colors microservice on premises and expose it
############################################################

.. image:: ../pictures/lab3/archi-lab3.png
   :align: center

|
Deploy Colors on private on-premises AKS
****************************************

* Connect to ``Jumphost`` and run the Colors microservice manifest to deploy it into the private k8S.

  .. code-block:: terminal
      kubectk apply -f /home/ubuntu/k8s-deployment/aks-sentence-colors.yaml

.. note:: As you can notice, the Colors microservice is pushed as a NodePort

|
Configure the private VolteNode in UDF
**************************************

* Connect to the Volterra Node UI (admin/Volterra123)
* Do not change the password, go directly to ``Dashboard``
* Click Configure Now

  * If you haven't created a site token in Volt Console, do it Now
  * Fill all the fields as you want, but select ``kvm-multi-nic-voltmesh``
  * Do not set any Latitude/Longitude, we will do it in the VoltConsole
  * Save configuration

.. warning:: If nothing happens when you click SAVE, open the browser console, and check the error. Looks like there is a UI bug, and you need to check the box ``IP Settings Configuration``.

|
Discover the Colors service
***************************

* Create a service discovery
  * Select your site, upload the kubeconfig file from the jumphost (/.kube/config)
  * Select Site Local Network as the k8s API is on 10.1.1.x/24 network.
  * Don't forget to publish full FQDN to VIP

* You should see ``Colors`` service as a NodePort

.. note:: This can take several minutes to discover services.

|
Expose the microservice with F5 Distributed Cloud
*************************************************

* Create an Origin Pool targeting the discovered service
* Create an Internal LB, so that the Generator can reach the Colors service
  * FYI, the generator targets this fqdn ``sentence-colors.default``

.. note :: Test your deployment