Generate API Key
================

Creates a long term use API key to use in lieu of a password.
With this key you can login using your user name and the key, instead of the account password.
If the account you have specified has one pre-existing, it is returned to you.
Setting **force_new** explicitly requests that an additional key be created for the account
even if keys already exist.

**HTTP Method**

.. http:get:: /api/account/generate_api_key

**Query String Parameters** - Required

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| v                | `Description`    | The version of the API to use                             |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | 1-                                                        |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``v=1``                                                   |
+------------------+------------------+-----------------------------------------------------------+
| api_token        | `Description`    | The API token used for this session                       |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Hex String                                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``api_token=7ca5dc5c7cce449fb0fff719307e8f5f``            |
+------------------+------------------+-----------------------------------------------------------+
| account_id       | `Description`    | The username associated with this account                 |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | String                                                    |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``account_id=user@example.com``                           |
+------------------+------------------+-----------------------------------------------------------+

**Query String Parameters** - Optional

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| force_new        | `Description`    | Set to `true` if you want to always create a new API key  |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | true/false                                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Default Value`  | false                                                     |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``force_new=true``                                        |
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
|           |               |    "ApiKey" : "your new long term ApiKey"                                |
|           |               |  }                                                                       |
+-----------+---------------+--------------------------------------------------------------------------+
| 400       | `Description` | An error occurred                                                        |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | .. code-block:: javascript                                               |
|           |               |                                                                          |
|           |               |  {                                                                       |
|           |               |    "ErrorType": "ERROR_TYPE_ENUM",                                       |
|           |               |    "ErrorComment": "Description of error details.                        |
|           |               |     See Error Output Format."                                            |
|           |               |  }                                                                       |
+-----------+---------------+--------------------------------------------------------------------------+

**Example Requests**

.. sourcecode:: http

    GET /api/account/generate_api_key?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f HTTP/1.1
        &account_id=user@example.com&force_new=true
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: text/javascript

    { "ApiKey" : "7ca5dc5c7cce449fb0fff719307e8f5f" }