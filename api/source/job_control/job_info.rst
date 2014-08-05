Job Info
========

Get a list of all tasks done by an existing job.

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
| job_id           | `Description`    | The Id of the job for which job status is returned        |
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
|           |               | .. raw:: html                                                            |
|           |               |                                                                          |
|           |               |    See<a href="../output_formats/formats.html#job-info-format">          |
|           |               |    Job Info Format</a> for details.                                      |
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
|           |               | .. raw:: html                                                            |
|           |               |                                                                          |
|           |               |    See<a href="../output_formats/formats.html#error-format">             |
|           |               |    Error Format</a> for details.                                         |
|           |               |                                                                          |
+-----------+---------------+--------------------------------------------------------------------------+

**Example Requests**

.. sourcecode:: http

    GET /api/job/info?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f HTTP/1.1
        &job_id=64bea283eff6475ea6596027a6ba0929
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "JobId" : "64bea283eff6475ea6596027a6ba0929",
        "JobName" : "example_job",
        "Language" : "EN_US",
        "Tasks" :
        [{
            "TaskId" : "23D263A01C134455B6C73D8EC2E1D784",
            "TaskType" : "JOB_CREATED",
            "TaskRequestTime" : "2014-07-31T12:35:52Z",
            "TaskCompletionTime" : "2014-07-31T14:35:52Z",
            "TaskInfo" : "example_info",
            "TaskStatus" : "COMPLETE",
        }]
    }