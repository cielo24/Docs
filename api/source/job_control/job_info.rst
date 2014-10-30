Job Info
========

Get a list of all tasks associated with an existing job.

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
        "StartDate": "2014-08-27T14:00:06.472706",
        "TargetLanguage": "en",
        "MediaLengthSeconds": 607.81,
        "Language": "EN_US",
        "SourceLanguage": "en",
        "ReturnTargets": {},
        "CompletedDate": "2014-08-27T14:10:41.923125",
        "JobStatus": "RETURNED",
        "JobId": "d4fb871e07514304b23131b45f8caa1f",
        "Priority": "STANDARD",
        "DueDate": "2014-08-29T14:00:06.472706",
        "Tasks": [
            {
                "TaskId" : "23D263A01C134455B6C73D8EC2E1D784",
                "TaskType" : "JOB_CREATED",
                "TaskRequestTime" : "2014-07-31T12:35:52Z",
                "TaskCompletionTime" : "2014-07-31T14:35:52Z",
                "TaskInfo" : "example_info",
                "TaskStatus" : "COMPLETE",
            }
        ],
        "ExternalID": "",
        "CreationDate": "2014-08-27T14:00:06.472706",
        "Fidelity": "MECHANICAL",
        "JobName": "example_job",
        "Options": {},
        "TurnaroundTimeHours": 48
    }
