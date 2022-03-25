Lab 1 - Apply Shape Bot Defense protection
##########################################

In the first module, we created and applied a WAAP policy with the Basic Bot Protection. This protection is based on Bot Signature only. There is no JS or challenge sent to the source.

**F5XC Shape Bot Protection** is the connector (similar to Shape IBD on BIG-IP) in order to inject the famous Shape JS and collect device signals. Then, Shape infrastructure allows or denies access to the application

.. image:: ../pictures/lab1/IBD.png
   :align: center

|

Enable Shape Bot Protection on protected endpoints
**************************************************

In the previous lab, we managed to query and buy stocks from a CURL command. This CURL targeted the endpoint ``/trading/rest/buy_stocks.php`` and bought F5 stocks.

Now, let's protect this endpoint so that the CURL will be blocked, but not the legetimate requests from a browser.

* Edit your HTTPS LB from lab 1 (HTTPS LB on RE only) - Or any other if you prefer.
* Enable ``Bot Defense``
* Select US (EU not yet available) and ``Show Advanced Fields``
* Extend ``Timeout`` to 1500 (because pipelines located in US)

* Create a new ``Bot Defense Policy``
* Create a new ``Protected App Endpoints``
* Add a new item and configure as below. This is the Buy Stock URL.

|

  .. image:: ../pictures/lab1/rule.png
     :align: center
     :scale: 50%

* Save and keep default settings for the JS injection
* Save and Apply your HTTP LB

|

Test your Bot Defense Protection
********************************

* Connect to your HTTPS LB with a browser (incognito - private mode) and buy new stocks
* Now, run the below CURL 

  * For Mac Users

  .. code-block:: bash

    curl 'https://<TO_BE_REPLACED_BY_YOUR_FQDN>/trading/rest/buy_stocks.php' \
    -H 'authorization: Basic YWRtaW46aWxvdmVibHVl' \
    -H 'user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/96.0.4664.110 Safari/537.36' \
    -H 'content-type: application/json; charset=UTF-8' \
    -H 'x-requested-with: XMLHttpRequest' \
    --data-raw '{"trans_value":330,"qty":2,"company":"FFIV","action":"buy","stock_price":165}' \
    --compressed    

  * For Windows Users

  .. code-block:: bash

    curl --location --request POST "https://<TO_BE_REPLACED_BY_YOUR_FQDN>/trading/rest/buy_stocks.php" --header "authorization: Basic YWRtaW46YWRtaW4uRjVkZW1vLmNvbQ==" --header "user-agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/96.0.4664.110 Safari/537.36" --header "content-type: application/json; charset=UTF-8" --header "x-requested-with: XMLHttpRequest" --header "Cookie: 3ba01=3b7f08b7c6ff531030e6f43656582f0b000004c246698307ddbe" --data-raw "{\"trans_value\": 330,\"qty\": 2,\"company\": \"FFIV\",\"action\": \"buy\",\"stock_price\": 165}"


* The call should be blocked

|

Check your analytics
********************

* Now, go to your LB ``Security Analytics``
* Go to ``Bot Traffic overview`` and check if you see a Human and Bot event logs

  .. image:: ../pictures/lab1/analytics.png
     :align: center


.. warning:: End of the SE/Partner/Customer F5XC WAAP foundational

   