Add Media To Job
================

Add a piece of media to an existing job.
A job may only have a single piece of media associated with it,
attempting to add additional media will return an error code.

To add media from a publicly accessible URL,
make a GET request and specify the URL in the **media_url** parameter.

To add media from a local file, make a POST request.
Do NOT specify the media_url parameter in the request URL.
No content-type should be included in the HTTP header.
Upload the media directly inline as the body of the request.
The media should be uploaded as raw binary, no encoding (base64, hex, etc) is required.
Chunk-transfer encoding is NOT supported. If uploading large files (500 mb and up),
specify the Content-Length in the header.

**HTTP Method**

.. http:get:: /api/job/add_media (from URL)

.. http:post:: /api/job/add_media (from local file)

**Query String Parameters** - Required (always)

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
| job_id           | `Description`    | The ID of the job to which media is added                 |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Hex String                                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``job_id=64bea283eff6475ea6596027a6ba0929``               |
+------------------+------------------+-----------------------------------------------------------+

**Query String Parameters** - Required `(when adding media from URL)`

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| media_url        | `Description`    | The URL from which media will be obtained                 |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | URL Encoded String                                        |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``media_url=http%3A%2F%2Fwww.domain.com%2Fvideo.mp4``     |
+------------------+------------------+-----------------------------------------------------------+

**Request Body** - Required `(when adding media from local file)`

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| not applicable   | `Description`    | Raw binary of a media file                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | not applicable                                            |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | not applicable                                            |
+------------------+------------------+-----------------------------------------------------------+

**HTTP Headers** - Required `(when uploading LARGE media files)`

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| Content-Length   | `Description`    | File size (in bytes)                                      |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Integer                                                   |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``645809838``                                             |
+------------------+------------------+-----------------------------------------------------------+

**Responses**

+-----------+-------------------------------------------------------------------------------------+
| HTTP Code | Details                                                                             |
+===========+===============+=====================================================================+
| 200       | `Description` | Success                                                             |
|           +---------------+---------------------------------------------------------------------+
|           | `Contents`    | .. code-block:: javascript                                          |
|           |               |                                                                     |
|           |               |  {                                                                  |
|           |               |    "TaskId" : "Encoded Task ID"                                     |
|           |               |  }                                                                  |
+-----------+---------------+---------------------------------------------------------------------+
| 400       | `Description` | An error occurred                                                   |
|           +---------------+---------------------------------------------------------------------+
|           | `Contents`    | .. code-block:: javascript                                          |
|           |               |                                                                     |
|           |               |  {                                                                  |
|           |               |    "ErrorType": "ERROR_TYPE_ENUM",                                  |
|           |               |    "ErrorComment": "Description of error details."                  |
|           |               |  }                                                                  |
|           |               |                                                                     |
|           |               | .. container::                                                      |
|           |               |                                                                     |
|           |               |    See :ref:`error-format-label` for details.                       |
|           |               |                                                                     |
+-----------+---------------+---------------------------------------------------------------------+

**Example Requests**

.. sourcecode:: http

    GET /api/job/add_media?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &job_id=64bea283eff6475ea6596027a6ba0929
    &media_url=http%3A%2F%2Fwww.domain.com%2Fvideo.mp4 HTTP/1.1
    Host: api.cielo24.com

.. sourcecode:: http

    POST /api/job/add_media?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &job_id=64bea283eff6475ea6596027a6ba0929 HTTP/1.1
    Host: api.cielo24.com
    Content-Length: 645809838
    Body: raw binary

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    { "TaskId" : "41ec7d23fb4b45f9b48a13d0b7283bf2" }