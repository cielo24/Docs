Job List
========

Get a list of all ACTIVE jobs associated with the user account that generated the given API Token.
The list is sorted by default to the creation time of the job, descending.

**HTTP Method**

.. http:get:: /api/job/list

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

**Responses**

+-----------+------------------------------------------------------------------------------------------+
| HTTP Code | Details                                                                                  |
+===========+===============+==========================================================================+
| 200       | `Description` | Success                                                                  |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | .. code-block:: javascript                                               |
|           |               |                                                                          |
|           |               |  JSON formatted Job List.                                                |
|           |               |                                                                          |
|           |               | .. container::                                                           |
|           |               |                                                                          |
|           |               |    See :ref:`job-list-format-label` for details.                         |
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

    GET /api/job/list?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f HTTP/1.1
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "Username" : "john_doe",
        "ActiveJobs" :
        [{
            "StartDate": "2014-08-27T14:00:06.472706",
            "TargetLanguage": "EN_US",
            "MediaLengthSeconds": 607.81,
            "SourceLanguage": "en",
            "TurnarondTimeHours": 48,
            "ReturnTargets": "",
            "CompletedDate": "2014-08-27T14:10:41.923125",
            "CreationTime": "2014-08-27T14:00:06.472706",
            "CompletedTime": "2014-08-27T14:10:41.923125",
            "JobStatus": "Complete",
            "JobId": "d4fb871e07514304b23131b45f8caa1f",
            "Priority": "STANDARD",
            "DueDate": "2014-08-29T14:00:06.472706",
            "ExternalID": "",
            "CreationDate": "2014-08-27T14:00:06.472706",
            "StartTime": "2014-08-27T14:00:06.472706",
            "Fidelity": "MECHANICAL",
            "JobName": "example_job",
            "JobLanguage": "EN_US",
            "Options": {},
            "TurnaroundTimeHours": 48
        }]
    }
