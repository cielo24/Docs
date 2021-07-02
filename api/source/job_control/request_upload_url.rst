Request Pre-signed Upload URL
================

Generates special expirable URL for direct media content upload.
Use this endpoint when you need to upload local files.
For media where a public URL is available, consider using the "add_media_url" endpoint instead.
After calling this endpoint, you will receive a signed URL in the response. The next step is to perform a "PUT" request to this URL.
URLs have a lifetime of 12 hours.  Note: when performing the "PUT" request on the pre-signed URL, make sure to omit the 
authorization header.  When your upload is complete, perform the standard "POST" request to the "perform_transcription" endpoint to begin processing.

**HTTP Method**

.. http:get:: /api/job/request_upload_url

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

**Request Body** — `(when adding media from local file)`

not applicable

**HTTP Headers** — Required `(when uploading LARGE media files)`

not applicable
**Responses**

+-----------+-------------------------------------------------------------------------------------+
| HTTP Code | Details                                                                             |
+===========+===============+=====================================================================+
| 200       | `Description` | Success                                                             |
|           +---------------+---------------------------------------------------------------------+
|           | `Contents`    | .. code-block:: javascript                                          |
|           |               |                                                                     |
|           |               |  {                                                                  |
|           |               |    "upload_url" : "https://some-url"                                |
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

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json
    { "upload_url" : "https://..." }