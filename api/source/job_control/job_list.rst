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

+-------------------------+-----------------------------------------------------------------------+
| Name                    | Details                                                               |
+=========================+==================+====================================================+
| CompleteDateFrom        | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs that were completed on or after</br>    |
|                         |                  |  the specified date and time.                      |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``CompleteDateFrom=2014-08-27T13:40:53``           |
+-------------------------+------------------+----------------------------------------------------+
| CompleteDateTo          | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs that were completed on or before</br>   |
|                         |                  |  the specified date and time.                      |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``CompleteDateTo=2014-08-27T13:40:53``             |
+-------------------------+------------------+----------------------------------------------------+
| CreationDateFrom        | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs that were created on or after</br>      |
|                         |                  |  the specified date and time.                      |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``CreationDateFrom=2014-08-27T13:40:53``           |
+-------------------------+------------------+----------------------------------------------------+
| CreationDateTo          | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs that were created on or before</br>     |
|                         |                  |  the specified date and time.                      |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``CreationDateTo=2014-08-27T13:40:53``             |
+-------------------------+------------------+----------------------------------------------------+
| DueDateFrom             | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs that have a due date on or after</br>   |
|                         |                  |  the specified date and time.                      |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``DueDateFrom=2014-08-27T13:40:53``                |
+-------------------------+------------------+----------------------------------------------------+
| DueDateTo               | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs that have a due date on or before</br>  |
|                         |                  |  the specified date and time.                      |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``DueDateTo=2014-08-27T13:40:53``                  |
+-------------------------+------------------+----------------------------------------------------+
| Fidelity                | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs with the specified fidelity.            |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | String.                                            |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``Fidelity=MECHANICAL``                            |
+-------------------------+------------------+----------------------------------------------------+
| JobStatus               | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs with the specified status.              |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | String.                                            |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``JobStatus=Complete``                             |
+-------------------------+------------------+----------------------------------------------------+
| Priority                | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs with the specified priority.            |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | String.                                            |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``Priority=STANDARD``                              |
+-------------------------+------------------+----------------------------------------------------+
| ReturnDateFrom          | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs that were returned on or after</br>     |
|                         |                  |  the specified date and time. Return dates are     |
|                         |                  |  usually the same as Complete dates, but may       |
|                         |                  |  differ if your account is configured for Customer |
|                         |                  |  Review or Manual Return.                          |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``ReturnDateFrom=2014-08-27T13:40:53``             |
+-------------------------+------------------+----------------------------------------------------+
| ReturnDateTo            | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs that were returned on or before</br>    |
|                         |                  |  the specified date and time.                      |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``ReturnDateTo=2014-08-27T13:40:53``               |
+-------------------------+------------------+----------------------------------------------------+
| StartDateFrom           | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs that were started on or after</br>      |
|                         |                  |  the specified date and time.                      |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``StartDateFrom=2014-08-27T13:40:53``              |
+-------------------------+------------------+----------------------------------------------------+
| StartDateTo             | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs that were started on or before</br>     |
|                         |                  |  the specified date and time.                      |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``StartDateTo=2014-08-27T13:40:53``                |
+-------------------------+------------------+----------------------------------------------------+
| TurnaroundTimeHoursFrom | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs that have a turnaround time</br>        |
|                         |                  |  on or after the specified hour.                   |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | Integer.                                           |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``TurnaroundTimeHoursFrom=24``                     |
+-------------------------+------------------+----------------------------------------------------+
| TurnaroundTimeHoursTo   | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs that have a turnaround time</br>        |
|                         |                  |  on or before the specified hour.                  |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | Integer.                                           |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``TurnaroundTimeHoursTo=48``                       |
+-------------------------+------------------+----------------------------------------------------+
| Username                | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List jobs that are owned by the specified</br>    |
|                         |                  |  sub-account. Pass '*' to list all jobs</br>       |
|                         |                  |  owned by the logged in account and all</br>       |
|                         |                  |  of its descendants.                               |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | String.                                            |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``myaccountname``                                  |
+-------------------------+------------------+----------------------------------------------------+

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

    GET /api/job/list?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f&Priority=STANDARD HTTP/1.1
    Host: api.cielo24.com

.. sourcecode:: http

    GET /api/job/list?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &CompleteDateTo=2014-08-27T14%3A44%3A54 HTTP/1.1
    Host: api.cielo24.com

.. sourcecode:: http

    GET /api/job/list?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &CompleteDateTo=2014-08-27 HTTP/1.1
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "Username": "john_doe",
        "ActiveJobs":
        [{
            "JobId": "d4fb871e07514304b23131b45f8caa1f",
            "JobName": "example_job",
            "MediaLengthSeconds": 607.81,
            "ExternalID": "sample_id",
            "Priority": "STANDARD",
            "Fidelity": "MECHANICAL",
            "TurnaroundTimeHours": 48,
            "JobStatus": "Complete",
            "SourceLanguage": "en",
            "TargetLanguage": "en",
            "CreationDate": "2014-08-27T14:00:06.472706",
            "StartDate": "2014-08-27T14:00:06.472706",
            "DueDate": "2014-08-29T14:00:06.472706",
            "CompletedDate": "2014-08-27T14:10:41.923125",
            "ReturnDate": "2014-08-27T14:10:42.885185",
            "ReturnTargets":  {
                "url": [
                    {
                        "callback_url": "https://sample-url.com/return/"
                    },
                    {
                        "callback_url": "https://sample-url-2.com/return/"
                    }
                ]
            },
            "Options": {}
        }]
    }
