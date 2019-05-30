list_related
========

Get both the leading job and a list of jobs related to the leading jobs

**HTTP Method**

.. http:get:: /api/job/list_related

**Query String Parameters** — Required

+------------------+------------------------------------------------------------------------------+
| Name             | Details                                                                      |
+==================+==================+===========================================================+
| job_id           | `Description`    | Unique identifier for either the leading job or related   |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Hex Sring                                                 |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``job_id=93n7dc5c7cce449fbk4h3nfo89m2be8w``               |
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
| 4xx       | `Description` | User input error occurred                                                |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | Error description (see :ref:`error-format-label` for details)            |
+-----------+---------------+--------------------------------------------------------------------------+
| 5xx       | `Description` | System error occurred                                                    |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | Error description (see :ref:`error-format-label` for details)            |
+-----------+---------------+--------------------------------------------------------------------------+

**Example Requests**

.. sourcecode:: http

GET /api/job/list_related?api_token=7ca5dc5c7cce449fb0fff719307e8f5f&job_id=93n7dc5c7cce449fbk4h3nfo89m2be8w
Host: api.cielo24.com

**Example Response**

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
      "related_jobs": [],
      "leading_job": {
        "job_status": "Pending",
        "job_id": "99ac39bc9fe344bea6a8fdb75afccbda",
        "current_priority": "STANDARD",
        "media_length": "0:10:22.844807",
        "current_fidelity": "HIGH",
        "language": "fr:en,fr"
      }
    }
