Get Media
=========

Get a URL to the media for an existing job. If the media was directly uploaded to the job, no URL will be returned.

**HTTP Method**

.. http:get:: /api/job/media

**Query String Parameters** - Required

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
| job_id           | `Description`    | The Id of the job                                         |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Hex String                                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``job_id=64bea283eff6475ea6596027a6ba0929``               |
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
|           |               |    "MediaUrl" : "Encoded Media Url"                                      |
|           |               |  }                                                                       |
+-----------+---------------+--------------------------------------------------------------------------+
| 400       | `Description` | An error occurred                                                        |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | .. code-block:: javascript                                               |
|           |               |                                                                          |
|           |               |  {                                                                       |
|           |               |    "ErrorType": "ERROR_TYPE_ENUM",                                       |
|           |               |    "ErrorComment": "Description of error details."                       |
|           |               |  }                                                                       |
|           |               |                                                                          |
|           |               | .. raw:: html                                                            |
|           |               |                                                                          |
|           |               |    See<a href="../output_formats/formats.html#error-format">             |
|           |               |    Error Format</a> for details.                                         |
|           |               |                                                                          |
+-----------+---------------+--------------------------------------------------------------------------+

**Example Requests**

.. sourcecode:: http

    GET /api/job/media?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f HTTP/1.1
        &job_id=64bea283eff6475ea6596027a6ba0929
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: text/javascript

    { "MediaUrl" : "https://fake.url.com" }