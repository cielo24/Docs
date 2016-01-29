Generate API Key
================

Creates a long term use API key to use in lieu of a password.
With this key you can :doc:`login <login>` using your user name and the key, instead of the account password.
If the account you have specified has one pre-existing, it is returned to you.
Setting **force_new** explicitly requests that an additional key be created for the account
even if keys already exist.

**HTTP Method**

.. http:get:: /api/account/generate_api_key

**Query String Parameters** — Required

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| v                | `Description`    | The version of the API to use                             |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | 1                                                         |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``v=1``                                                   |
+------------------+------------------+-----------------------------------------------------------+
| api_token        | `Description`    | The API token used for this session                       |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Hex String                                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``api_token=7ca5dc5c7cce449fb0fff719307e8f5f``            |
+------------------+------------------+-----------------------------------------------------------+

**Query String Parameters** — Optional

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| force_new        | `Description`    | Set to `true` if you want to always create a new API key  |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Boolean                                                   |
|                  +------------------+-----------------------------------------------------------+
|                  | `Default Value`  | false                                                     |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``force_new=true``                                        |
+------------------+------------------+-----------------------------------------------------------+
| account_id       | `Description`    | Username of a sub account for which to generate a key     |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | String                                                    |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``account_id=my_sub_account``                             |
+------------------+------------------+-----------------------------------------------------------+

**Responses**

+-----------+------------------------------------------------------------------------------------------+
| HTTP Code | Details                                                                                  |
+===========+===============+==========================================================================+
| 200       | `Description` | Success                                                                  |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | .. code-block:: javascript                                               |
|           |               |                                                                          |
|           |               |  {                                                                       |
|           |               |    "ApiKey": "The new long term ApiKey"                                  |
|           |               |  }                                                                       |
+-----------+---------------+--------------------------------------------------------------------------+
| 400       | `Description` | An error occurred                                                        |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | Error description (see :ref:`error-format-label` for details)            |
+-----------+---------------+--------------------------------------------------------------------------+

**Example Requests**

.. sourcecode:: http

    GET /api/account/generate_api_key?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &account_id=john_doe&force_new=true HTTP/1.1
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    { "ApiKey" : "7ca5dc5c7cce449fb0fff719307e8f5f" }