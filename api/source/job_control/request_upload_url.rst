Request Pre-signed Upload URL
================

Generates special expirable URL for direct media content upload.
Use this endpoint when you need to upload local files.
For media where a public URL is available, consider using the "add_media_url" endpoint instead.
After calling this endpoint, you will receive a signed URL in the response. The next step is to perform a "PUT" request to this URL.
When your upload is complete, perform the standard "POST" request to the "perform_transcription" endpoint to begin processing.
URLs have a lifetime of 48 hours.

**HTTP Method**

.. http:get:: /api/job/request_upload_url (from URL)

.. http:post:: /api/job/request_upload_url (from local file)

**Query String Parameters** — Required (always)

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

**Query String Parameters** — Required `(when adding media from URL)`

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| media_url        | `Description`    | The URL from which media will be obtained                 |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | URL Encoded String                                        |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``media_url=http%3A%2F%2Fwww.domain.com%2Fvideo.mp4``     |
+------------------+------------------+-----------------------------------------------------------+

**Request Body** — `(when adding media from local file)`

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| not applicable   | `Description`    | Raw binary of a media file                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | not applicable                                            |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | not applicable                                            |
+------------------+------------------+-----------------------------------------------------------+

**HTTP Headers** — Required `(when uploading LARGE media files)`

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
|           | `Contents`    | Error description (see :ref:`error-format-label` for details)       |
+-----------+---------------+---------------------------------------------------------------------+

**Example Requests**

.. sourcecode:: http

    GET /api/job/request_upload_url?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &job_id=64bea283eff6475ea6596027a6ba0929
    &media_url=http%3A%2F%2Fwww.domain.com%2Fvideo.mp4 HTTP/1.1
    Host: api.cielo24.com

.. sourcecode:: http

    POST /api/job/request_upload_url?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &job_id=64bea283eff6475ea6596027a6ba0929 HTTP/1.1
    Host: api.cielo24.com
    Content-Length: 645809838
    Body: raw binary

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json
    { "upload_url" : "signed-url" }