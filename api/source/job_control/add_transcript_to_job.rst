Add transcript To Job
================

Add a transcript to an existing job.

**not supported for every workflow, talk to your account manager for more details before using this feature**

To add transcript from a publicly accessible URL,
make a GET request and specify the URL in the **transcript_url** parameter.

To add transcript from a local file, make a POST request.
Do NOT specify the transcript_url parameter in the request URL.
No content-type should be included in the HTTP header.
Upload the transcript directly inline as the body of the request.
The transcript should be uploaded as raw binary, no encoding (base64, hex, etc) is required.
Chunk-transfer encoding is NOT supported. If uploading large files (500 mb and up),
specify the Content-Length in the header. File size is limited to 10 gb.

**HTTP Method**

.. http:get:: /api/job/add_transcript (from URL)

.. http:post:: /api/job/add_transcript (from local file)

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
| job_id           | `Description`    | The ID of the job to which transcript is added            |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Hex String                                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``job_id=64bea283eff6475ea6596027a6ba0929``               |
+------------------+------------------+-----------------------------------------------------------+
| format           | `Description`    | The format of the transcription file                      |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | String `text` or `srt`                                    |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``format=text``                                           |
+------------------+------------------+-----------------------------------------------------------+

**Query String Parameters** — Required `(when adding transcript from URL)`

+------------------+-------------------------------------------------------------------------------------+
| Name             | Details                                                                             |
+==================+==================+==================================================================+
| transcript_url   | `Description`    | The URL from which transcript will be obtained                   |
|                  +------------------+------------------------------------------------------------------+
|                  | `Allowed Values` | URL Encoded String                                               |
|                  +------------------+------------------------------------------------------------------+
|                  | `Example`        | ``transcript_url=http%3A%2F%2Fwww.domain.com%2Fvideo_script.txt``|
+------------------+------------------+------------------------------------------------------------------+

**Request Body** — Required `(when adding transcript from local file)`

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| not applicable   | `Description`    | Raw binary of a transcript file                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | not applicable                                            |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | not applicable                                            |
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

    GET /api/job/add_transcript?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &job_id=64bea283eff6475ea6596027a6ba0929
    &transcript_url=http%3A%2F%2Fwww.domain.com%2Fvideo_script.txt HTTP/1.1
    Host: api.cielo24.com

.. sourcecode:: http

    POST /api/job/add_transcript?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &job_id=64bea283eff6475ea6596027a6ba0929 HTTP/1.1
    Host: api.cielo24.com
    Content-Length: 645809838
    Body: raw binary

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    { "TaskId" : "41ec7d23fb4b45f9b48a13d0b7283bf2" }
