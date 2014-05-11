Login
=====

Login to the cielo24 API to obtain an API access token for use when calling other methods.
Optional arguments may be passed either as HTTP headers or query string parameters.
Required arguments must be passed as query string parameters.


**HTTP Method**

    .. http:get:: /api/account/login

**HTTP Headers** - Optional

Provide either x-auth-user and x-auth-key or just x-auth-securekey.

.. list-table::
   :widths: 6 15 4 25
   :header-rows: 1

   * - Name
     - Description
     - Allowed Values
     - Example
   * - x-auth-user
     - The username associated with this account
     - String
     - ``user@example``
   * - x-auth-key
     - The password associated with this account
     - String
     - ``ExamplePassword``
   * - x-auth-securekey
     - A long term security key generated via generate_api_key
     - Hex String
     - ``968a8b637a5040159424872fffdb895b``

**Query String Parameters** - Required

    .. list-table::
       :widths: 15 30 10 30
       :header-rows: 1

       * - Name
         - Description
         - Allowed Values
         - Example
       * - v
         - The version of the API to use.
         - 1-
         - ``v=1``

**Query String Parameters** - Optional
    Provide either username and password or just securekey.

    .. list-table::
       :widths: 15 30 10 30
       :header-rows: 1

       * - Name
         - Description
         - Allowed Values
         - Example
       * - username
         - The username associated with this account
         - String
         - ``username=user@example``
       * - password
         - The password associated with this account
         - String
         - ``password=ExamplePassword``
       * - securekey
         - A long term security key generated via generate_api_key
         - Hex String
         - ``secureKey=968a8b637a5040159424872fffdb895b``

**Responses**

    .. list-table::
        :widths: 5 10 30
        :header-rows: 1

        * - HTTP Code
          - Description
          - Contents
        * - 200
          - Success
          - .. sourcecode:: http

                {"ApiToken": "a hex string consisting of the new API token"}

        * - 4XX
          - An error occurred
          - .. sourcecode:: http

                {"ErrorType": "ERROR_TYPE_ENUM", "ErrorComment": "Description of error details. See Error Output Format"}

**Example Requests**

    .. sourcecode:: http

        GET /api/account/login?v=1?username=user@example&password=ExamplePassword HTTP/1.1
        Host: api.cielo24.com

    .. sourcecode:: http

        GET /api/account/login?v=1?securekey=968a8b637a5040159424872fffdb895b HTTP/1.1
        Host: api.cielo24.com

    .. sourcecode:: http

        GET /api/account/login?v=1 HTTP/1.1
        Host: api.cielo24.com
        x-auth-user: user@example
        x-auth-key: ExamplePassword

    .. sourcecode:: http

        GET /api/account/login?v=1 HTTP/1.1
        Host: api.cielo24.com
        x-auth-securekey: 968a8b637a5040159424872fffdb895b

**Example Response**

    .. sourcecode:: http

        HTTP/1.1 200 OK
        Content-Type: text/javascript

        {"ApiToken": "7ca5dc5c7cce449fb0fff719307e8f5f"}