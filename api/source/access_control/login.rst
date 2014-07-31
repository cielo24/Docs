Login
=====

Login to the cielo24 API to obtain an API access token for use when calling other methods.
Optional arguments may be passed either as HTTP headers or query string parameters.
Required arguments must be passed as query string parameters.


**HTTP Method**

.. http:get:: /api/account/login

**HTTP Headers** - Optional

Provide **x-auth-user** with either **x-auth-key** or **x-auth-securekey**.

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| x-auth-user      | `Description`    | The username associated with this account                 |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | String                                                    |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``user@example.com``                                      |
+------------------+------------------+-----------------------------------------------------------+
| x-auth-password  | `Description`    | The password associated with this account                 |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | String                                                    |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``example_password``                                      |
+------------------+------------------+-----------------------------------------------------------+
| x-auth-securekey | `Description`    | A long term security key generated via generate_api_key   |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Hex String                                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``968a8b637a5040159424872fffdb895b``                      |
+------------------+------------------+-----------------------------------------------------------+

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

**Query String Parameters** - Optional

    Provide **username** with either **password** or **securekey**.

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| username         | `Description`    | The username associated with this account                 |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | String                                                    |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``username=user@example.com``                             |
+------------------+------------------+-----------------------------------------------------------+
| password         | `Description`    | The password associated with this account                 |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | String                                                    |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``password=example_password``                             |
+------------------+------------------+-----------------------------------------------------------+
| securekey        | `Description`    | A long term security key generated via generate_api_key   |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Hex String                                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``securekey=968a8b637a5040159424872fffdb895b``            |
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
|           |               |    "ApiToken": "a hex string consisting of the new API token"            |
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

    GET /api/account/login?v=1&username=user@example.com&password=example_password HTTP/1.1
    Host: api.cielo24.com

.. sourcecode:: http

    GET /api/account/login?v=1&username=user&securekey=968a8b637a5040159424872fffdb895b HTTP/1.1
    Host: api.cielo24.com

.. sourcecode:: http

    GET /api/account/login?v=1 HTTP/1.1
    Host: api.cielo24.com
    x-auth-user: user@example.com
    x-auth-key: example_password

.. sourcecode:: http

    GET /api/account/login?v=1 HTTP/1.1
    Host: api.cielo24.com
    x-auth-user: user@example.com
    x-auth-securekey: 968a8b637a5040159424872fffdb895b

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: text/javascript

    { "ApiToken" : "7ca5dc5c7cce449fb0fff719307e8f5f" }