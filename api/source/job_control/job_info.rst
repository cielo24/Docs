Job Info
========

Get information about an existing job.

**HTTP Method**

.. http:get:: /api/job/info

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
| job_id           | `Description`    | The ID of the job for which job status is returned        |
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
|           |               |  JSON formatted job status.                                              |
|           |               |                                                                          |
|           |               | .. container::                                                           |
|           |               |                                                                          |
|           |               |    See :ref:`job-info-format-label` for details.                         |
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

    GET /api/job/info?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &job_id=64bea283eff6475ea6596027a6ba0929 HTTP/1.1
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "JobId": "d4fb871e07514304b23131b45f8caa1f",
        "JobName": "example_job",
        "MediaLengthSeconds": 607.81,
        "ExternalID": "sample_id",
        "Priority": "STANDARD",
        "Fidelity": "MECHANICAL",
        "JobStatus": "Complete",
        "SourceLanguage": "en",
        "TargetLanguage": "en",
        "CreationDate": "2014-08-27T14:00:06.472706",
        "StartDate": "2014-08-27T14:00:06.472706",
        "DueDate": "2014-08-29T14:00:06.472706",
        "CompletedDate": "2014-08-27T14:10:41.923125",
        "ReturnDate": "2014-08-27T14:10:42.885185",
        "AuthorizationDate": "2014-08-27T14:00:06.472706",
        "JobDifficulty": "Unknown",
        "ReturnTargets": {
            "url": [
                {
                    "callback_url": "https://sample-url.com/return/"
                },
                {
                    "callback_url": "https://sample-url-2.com/return/"
                }
            ]
        },
        "Options": {
            "option_name": {
                "label": "option_label",
                "setting": "option_setting"
            }
        }
    }
