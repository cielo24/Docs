Aggregate Statistics
====================

Get aggregate statistics for the user account.
The statistics can be aggregated for the requester's account and/or its sub-accounts,
grouped by week or month and filtered by a certain time range.

**HTTP Method**

.. http:get:: /api/job/aggregate_statistics

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
| account_id              | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  Username of a sub account for which to</br>       |
|                         |                  |  return statistics. When unset, the call</br>      |
|                         |                  |  will return statistics for the requester's </br>  |
|                         |                  |  account. When set to *, the call will return</br> |
|                         |                  |  statistics for both requester's account</br>      |
|                         |                  |  and its sub-accounts.                             |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | String                                             |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``account_id=my_sub_account``                      |
+-------------------------+------------------+----------------------------------------------------+
| metrics                 | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  List of metrics for which to calculate</br>       |
|                         |                  |  statistics. When unset, will return data for</br> |
|                         |                  |  all available metrics.</br>                       |
|                         |                  |  Currently supported metrics:</br>                 |
|                         |                  |  -`billable_minutes`                               |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | JSON array of strings                              |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``metrics=["billable_minutes"]``                   |
+-------------------------+------------------+----------------------------------------------------+
| group_by                | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  Defines how to segment the calculations.</br>     |
|                         |                  |  When unset, will return a single segment</br>     |
|                         |                  |  over the specified time range.                    |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | ["week", "month"]                                  |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``group_by=month``                                 |
+-------------------------+------------------+----------------------------------------------------+
| start_date              | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  Will calculate statistics for jobs returned</br>  |
|                         |                  |  after the specified date.                         |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``start_date=2014-08-27T13:40:53``                 |
+-------------------------+------------------+----------------------------------------------------+
| end_date                | `Description`    | .. raw:: html                                      |
|                         |                  |                                                    |
|                         |                  |  Will calculate statistics for jobs returned</br>  |
|                         |                  |  before the specified date.                        |
|                         |                  |                                                    |
|                         +------------------+----------------------------------------------------+
|                         | `Allowed Values` | Date in ISO format.                                |
|                         +------------------+----------------------------------------------------+
|                         | `Example`        | ``end_date=2014-08-27T13:40:53``                   |
+-------------------------+------------------+----------------------------------------------------+

**Responses**

+-----------+------------------------------------------------------------------------------------------+
| HTTP Code | Details                                                                                  |
+===========+===============+==========================================================================+
| 200       | `Description` | Success                                                                  |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | .. code-block:: javascript                                               |
|           |               |                                                                          |
|           |               |  JSON formatted statistics.                                              |
|           |               |                                                                          |
|           |               | .. container::                                                           |
|           |               |                                                                          |
|           |               |    See below for details.                                                |
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

    GET /api/job/aggregate_statistics?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f HTTP/1.1
    Host: api.cielo24.com

.. sourcecode:: http

    GET /api/job/aggregate_statistics?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f HTTP/1.1
    &metrics=["billable_minutes"]&account_id=*&group_by=month
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {
        "data": [
            {
                "billable_minutes": 4.0,
                "start_date": "2015-02-01T00:00:00",
                "end_date": "2015-02-28T00:00:00"
            },
            {
                "billable_minutes": 40.0,
                "start_date": "2015-03-01T00:00:00",
                "end_date": "2015-03-31T00:00:00"
            },
            {
                "billable_minutes": 1.0,
                "start_date": "2015-04-01T00:00:00",
                "end_date": "2015-04-30T00:00:00"
            },
            {
                "billable_minutes": 3.0,
                "start_date": "2015-05-01T00:00:00",
                "end_date": "2015-05-31T00:00:00"
            },
            {
                "billable_minutes": 1.0,
                "start_date": "2015-07-01T00:00:00",
                "end_date": "2015-07-31T00:00:00"
            }
        ],
        "start_date": null,
        "end_date": null
    }
