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

**Query String Parameters for filtering** - Optional

+-------------------------+---------------------------------------------------------------------------------------------+
| Name                    | Details                                                                                     |
+=========================+==================+==========================================================================+
| CreationDateFrom        | `Description`    | Filter jobs that were created on or after a particular date and time.    |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                                      |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Example`        | ``CreationDateFrom=2014-08-27T13:40:53``                                 |
+-------------------------+------------------+--------------------------------------------------------------------------+
| CreationDateTo          | `Description`    | Filter jobs that were created on or before a particular date and time.   |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                                      |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Example`        | ``CreationDateTo=2014-08-27T13:40:53``                                   |
+-------------------------+------------------+--------------------------------------------------------------------------+
| StartDateFrom           | `Description`    | Filter jobs that were started on or after a particular date and time.    |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                                      |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Example`        | ``StartDateFrom=2014-08-27T13:40:53``                                    |
+-------------------------+------------------+--------------------------------------------------------------------------+
| StartDateTo             | `Description`    | Filter jobs that were started on or before a particular date and time.   |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                                      |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Example`        | ``StartDateTo=2014-08-27T13:40:53``                                      |
+-------------------------+------------------+--------------------------------------------------------------------------+
| DueDateFrom             | `Description`    | Filter jobs that have a due date on or after a particular date and time. |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                                      |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Example`        | ``DueDateFrom=2014-08-27T13:40:53``                                      |
+-------------------------+------------------+--------------------------------------------------------------------------+
| DueDateTo               | `Description`    | Filter jobs that have a due date on or before a particular date and time.|
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                                      |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Example`        | ``DueDateTo=2014-08-27T13:40:53``                                        |
+-------------------------+------------------+--------------------------------------------------------------------------+
| CompleteDateFrom        | `Description`    | Filter jobs that were completed on or after a particular date and time.  |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                                      |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Example`        | ``CompleteDateFrom=2014-08-27T13:40:53``                                 |
+-------------------------+------------------+--------------------------------------------------------------------------+
| CompleteDateTo          | `Description`    | Filter jobs that were completed on or before a particular date and time. |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                                      |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Example`        | ``CompleteDateTo=2014-08-27T13:40:53``                                   |
+-------------------------+------------------+--------------------------------------------------------------------------+
| JobStatus               | `Description`    | Filter jobs by the status.                                               |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Allowed Values` | String.                                                                  |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Example`        | ``JobStatus=Complete``                                                   |
+-------------------------+------------------+--------------------------------------------------------------------------+
| Fidelity                | `Description`    | Filter jobs by the fidelity.                                             |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Allowed Values` | String.                                                                  |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Example`        | ``Fidelity=MECHANICAL``                                                  |
+-------------------------+------------------+--------------------------------------------------------------------------+
| Priority                | `Description`    | Filter jobs by the priority.                                             |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Allowed Values` | String.                                                                  |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Example`        | ``Priority=STANDARD``                                                    |
+-------------------------+------------------+--------------------------------------------------------------------------+
| TurnaroundTimeHoursFrom | `Description`    | Filter jobs that have a turnaround time on or after a particular digit.  |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Allowed Values` | Integer.                                                                 |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Example`        | ``TurnaroundTimeHoursFrom=24``                                           |
+-------------------------+------------------+--------------------------------------------------------------------------+
| TurnaroundTimeHoursTo   | `Description`    | Filter jobs that have a turnaround time on or before a particular digit. |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Allowed Values` | Integer.                                                                 |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Example`        | ``TurnaroundTimeHoursTo=48``                                             |
+-------------------------+------------------+--------------------------------------------------------------------------+
| Username                | `Description`    | List jobs that are owned by the specified sub-account. Pass '*' to list  |
|                         |                  | all jobs owned by the logged in account and all of its descendants.      |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Allowed Values` | String.                                                                  |
|                         +------------------+--------------------------------------------------------------------------+
|                         | `Example`        | ``myaccountname``                                                        |
+-------------------------+------------------+--------------------------------------------------------------------------+

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

.. sourcecode:: http

    GET /api/job/list?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f&Priority=ECONOMY HTTP/1.1
    Host: api.cielo24.com

.. sourcecode:: http

    GET /api/job/list?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f&CompleteDateTo=2014-08-27T14:44:54 HTTP/1.1
    Host: api.cielo24.com

.. sourcecode:: http

    GET /api/job/list?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f&CompleteDateTo=2014-08-27 HTTP/1.1
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "Username": "john_doe",
        "ActiveJobs":
        [{
            "StartDate": "2014-08-27T14:00:06.472706",
            "TargetLanguage": "EN_US",
            "MediaLengthSeconds": 607.81,
            "SourceLanguage": "en",
            "TurnaroundTimeHours": 48,
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
            "Options": {}
        }]
    }
