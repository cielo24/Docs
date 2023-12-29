Download Media
==============

Downloads transcoded/generated media.
Depending on the use-case of the job, there can be a number of
transcoded flavors of the original submitted video
unlike the **get_media** endpoint, this endpoint initiates a file download
If no media exists for the requested media_type, an error message will return.


**HTTP Method**

.. http:get:: /api/job/download_media

**Query String Parameters** -- Required

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| media_type       | `Description`    | Flavor of media to download                               |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | mp3, mp4                                                  |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``media_type=mp3``                                        |
+------------------+------------------+-----------------------------------------------------------+
| api_token        | `Description`    | The API token used for this session                       |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Hex String                                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``api_token=7ca5dc5c7cce449fb0fff719307e8f5f``            |
+------------------+------------------+-----------------------------------------------------------+
| job_id           | `Description`    | The ID of the job                                         |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Hex String                                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``job_id=64bea283eff6475ea6596027a6ba0929``               |
+------------------+------------------+-----------------------------------------------------------+

**Query String Parameters** -- Optional

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| text_to_speech   | `Description`    | Flag that signals to download the                         |
|                  |                  | audio description text to speech                          |
|                  |                  |audio file generated for a job                             |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Url Encoded Boolean String                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``text_to_speech=t``                                      |
+------------------+------------------+-----------------------------------------------------------+

**Response**

+-----------+------------------------------------------------------------------------------------------+
| HTTP Code | Details                                                                                  |
+===========+===============+==========================================================================+
| 200       | `Description` | Success                                                                  |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | .. code-block:: javascript                                               |
|           |               |                                                                          |
|           |               |  media file as body data                                                 |
+-----------+---------------+--------------------------------------------------------------------------+
| 400       | `Description` | An error occurred                                                        |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | Error description (see :ref:`error-format-label` for details)            |
+-----------+---------------+--------------------------------------------------------------------------+

**Example Requests**

.. sourcecode:: http

    GET /api/job/download_media?api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &job_id=64bea283eff6475ea6596027a6ba0929&media_type=mp3 HTTP/1.1
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: audio/mp3
    Content-Disposition: attachment; filename="test_job.mp3"
    Content: --**File Content**--
