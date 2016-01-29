Get ElementList
===============

Get the ElementList for a job.
The job must have completed transcription before a caption can be downloaded.

**HTTP Method**

.. http:get:: /api/job/get_elementlist

**Query String Parameters** — Required

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
| job_id           | `Description`    | The ID of the job                                         |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Hex String                                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``job_id=64bea283eff6475ea6596027a6ba0929``               |
+------------------+------------------+-----------------------------------------------------------+

**Query String Parameters** — Optional

+---------------------+---------------------------------------------------------------------------+
| Name                | Details                                                                   |
+=====================+==================+========================================================+
| elementlist_version | `Description`    | The version of the ElementList to return               |
|                     +------------------+--------------------------------------------------------+
|                     | `Allowed Values` | ISO 8601 Date String                                   |
|                     +------------------+--------------------------------------------------------+
|                     | `Default Value`  | None (the latest version is returned)                  |
|                     +------------------+--------------------------------------------------------+
|                     | `Example`        | ``elementlist_version=2014-07-31T12:35:52Z``           |
+---------------------+------------------+--------------------------------------------------------+

**Responses**

+-----------+------------------------------------------------------------------------------------------+
| HTTP Code | Details                                                                                  |
+===========+===============+==========================================================================+
| 200       | `Description` | Success                                                                  |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | .. code-block:: javascript                                               |
|           |               |                                                                          |
|           |               |  JSON formatted ElementList.                                             |
|           |               |                                                                          |
|           |               | .. container::                                                           |
|           |               |                                                                          |
|           |               |    See :ref:`elementlist-label` for details.                             |
|           |               |                                                                          |
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
|           |               | .. container::                                                           |
|           |               |                                                                          |
|           |               |    See :ref:`error-format-label` for details.                            |
|           |               |                                                                          |
+-----------+---------------+--------------------------------------------------------------------------+

**Example Requests**

.. sourcecode:: http

    GET /api/job/get_elementlist?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &job_id=64bea283eff6475ea6596027a6ba0929 HTTP/1.1
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "version" : 3,
        "start_time" : 1120,
        "end_time" : 774960,
        "language" : "EN_US",
        "segments" :
        [{
            "sequences" :
            [{
                "tokens" :
                [{
                    "interpolated" : false,
                    "start_time" : 1120,
                    "end_time" : 1470,
                    "value" : "topic",
                    "type" : 0,
                    "display_as" : "Topic",
                    "tags" : []
                }],
                "interpolated" : false,
                "start_time" : 1120,
                "end_time" : 1470,
                "confidence_score" : 1.0
            }],
            "speaker_change" : false,
            "speaker_id" : false,
            "interpolated" : true,
            "start_time" : 1120,
            "end_time" : 3640
        "speakers" : []
    }