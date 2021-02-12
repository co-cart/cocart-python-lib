CoCart API - Python Client
===============================

A Python wrapper for the CoCart REST API. Easily interact with the CoCart REST API using this library.

.. image:: https://secure.travis-ci.org/co-cart/cocart-python-lib.svg
    :target: http://travis-ci.org/github/co-cart/cocart-python-lib

.. image:: https://img.shields.io/pypi/v/cocart.svg
    :target: https://pypi.python.org/pypi/CoCart


Installation
------------

.. code-block:: bash

    pip install cocart

Getting started
---------------

Check out the CoCart API endpoints and data that can be manipulated in http://cocart.github.io/cocart-rest-api-docs/.

Setup
-----

.. code-block:: python

    from cocart import CoCartAPI

    CoCartAPI = CoCartAPI(
        url="http://example.com"
    )

Options
~~~~~~~

+-----------------------+-------------+----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
|         Option        |     Type    | Required |                                              Description                                                                                                                            |
+=======================+=============+==========+=====================================================================================================================================================================================+
| ``url``               | ``string``  | yes      | Your Store URL, example: https://example.com/                                                                                                                                       |
+-----------------------+-------------+----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``consumer_key``      | ``string``  | yes      | Your API consumer key                                                                                                                                                               |
+-----------------------+-------------+----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``consumer_secret``   | ``string``  | yes      | Your API consumer secret                                                                                                                                                            |
+-----------------------+-------------+----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``version``           | ``string``  | no       | API version, default is ``cocart/v1``                                                                                                                                               |
+-----------------------+-------------+----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``wp_api``            | `String`    | no       | Custom WP REST API URL prefix, used to support custom prefixes created with the [rest_url_prefix](https://developer.wordpress.org/reference/functions/rest_get_url_prefix/) filter. |
+-----------------------+-------------+----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``timeout``           | ``integer`` | no       | Connection timeout, default is ``5``                                                                                                                                                |
+-----------------------+-------------+----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``verify_ssl``        | ``bool``    | no       | Verify SSL when connect, use this option as ``False`` when need to test with self-signed certificates                                                                               |
+-----------------------+-------------+----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``query_string_auth`` | ``bool``    | no       | Force Basic Authentication as query string when ``True`` and using under HTTPS, default is ``False``                                                                                |
+-----------------------+-------------+----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
| ``oauth_timestamp``   | ``integer`` | no       | Custom timestamp for requests made with oAuth1.0a                                                                                                                                   |
+-----------------------+-------------+----------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Methods
-------

+--------------+----------------+------------------------------------------------------------------+
|    Params    |      Type      |                           Description                            |
+==============+================+==================================================================+
| ``endpoint`` | ``string``     | CoCart API endpoint, example: ``get-cart`` or ``products``       |
+--------------+----------------+------------------------------------------------------------------+
| ``data``     | ``dictionary`` | Data that will be converted to JSON                              |
+--------------+----------------+------------------------------------------------------------------+
| ``**kwargs`` | ``dictionary`` | Accepts ``params``, also other Requests arguments                |
+--------------+----------------+------------------------------------------------------------------+

GET
~~~

- ``.get(endpoint, **kwargs)``

POST
~~~~

- ``.post(endpoint, data, **kwargs)``

PUT
~~~

- ``.put(endpoint, data), **kwargs``

DELETE
~~~~~~

- ``.delete(endpoint, **kwargs)``

OPTIONS
~~~~~~~

- ``.options(endpoint, **kwargs)``

Response
--------

All methods will return `Response <http://docs.python-requests.org/en/latest/api/#requests.Response>`_ object.

Request with `params` example
-----------------------------

.. code-block:: python

    from cocart import CoCartAPI

    CoCartAPI = CoCartAPI(
        url="http://example.com"
    )

    # Get example.
    print(CoCartAPI.get("get-cart").json())

    # Force delete example.
    print(CoCartAPI.delete("products/100", params={"force": True}).json())

    # Query example.
    print(CoCartAPI.get("products", params={"per_page": 20}).json())


Bug Reporting
-------------

If you think you have found a bug in the library, please [open a new issue](https://github.com/co-cart/cocart-js-lib/issues/new/choose) and I will do my best to help you out.

Changelog
---------

[See changelog for details](https://github.com/co-cart/cocart-python-lib/blob/master/CHANGELOG.md)

Credits
-------

CoCart is developed and maintained by [Sébastien Dumont](https://github.com/seb86).

---

[sebastiendumont.com](https://sebastiendumont.com) &nbsp;&middot;&nbsp;
GitHub [@seb86](https://github.com/seb86) &nbsp;&middot;&nbsp;
Twitter [@sebd86](https://twitter.com/sebd86)

<p align="center">
    <img src="https://raw.githubusercontent.com/seb86/my-open-source-readme-template/master/a-sebastien-dumont-production.png" width="353">
</p>