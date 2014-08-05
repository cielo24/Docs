Add Embedded Media To Job
=========================

Add a piece of media to an existing job via a non-direct URL.
Use this option to link to a video hosted by such providers as Youtube, or Vimeo.

**HTTP Method**

.. http:get:: /api/job/add_media_url

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
| media_url        | `Description`    | The URL from which media will be obtained                 |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | URL Encoded String                                        |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``media_url=http%3A%2F%2Fyoutu.be%2F5m5MPiL99Nc``         |
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
|           |               |    "TaskId" : "Encoded Task Id"                                          |
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

    GET /api/job/add_media_url?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f HTTP/1.1
        &job_id=64bea283eff6475ea6596027a6ba0929
        &media_url=http%3A%2F%2Fyoutu.be%2F5m5MPiL99Nc
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: text/javascript

    { "TaskId" : "41ec7d23fb4b45f9b48a13d0b7283bf2" }