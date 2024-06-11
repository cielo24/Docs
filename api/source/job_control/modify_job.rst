Modify Job
==========

Modify parameters of an already existing job. The job must be in *Authorization* state.

**HTTP Method**

.. http:post:: /api/job/modify

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
| job_id           | `Description`    | The ID of the job which is being modified                 |
|                  +------------------+-----------------------------------------------------------+
|                  | `Allowed Values` | Hex String                                                |
|                  +------------------+-----------------------------------------------------------+
|                  | `Example`        | ``job_id=64bea283eff6475ea6596027a6ba0929``               |
+------------------+------------------+-----------------------------------------------------------+

**Query String Parameters** — Optional

+------------------------+-----------------------------------------------------------------------------------------+
| Name                   | Details                                                                                 |
+========================+==================+======================================================================+
| transcription_fidelity | `Description`    | The desired fidelity of the transcription                            |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Allowed Values` | :ref:`fidelity-label`                                                |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Example`        | ``transcription_fidelity=PREMIUM``                                   |
+------------------------+------------------+----------------------------------------------------------------------+
| turnaround_hours       | `Description`    | The number of hours after which the job is returned                  |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Allowed Values` | Integer                                                              |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Example`        | ``turnaround_hours=36``                                              |
+------------------------+------------------+----------------------------------------------------------------------+
| priority               | `Description`    | The desired priority of the transcription                            |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Allowed Values` | :ref:`priority-label`                                                |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Example`        | ``priority=STANDARD``                                                |
+------------------------+------------------+----------------------------------------------------------------------+
| account_id             | `Description`    | The username of the account to be assigned to the job                |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Allowed Values` | String                                                               |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Example`        | ``account_id=john_doe``                                              |
+------------------------+------------------+----------------------------------------------------------------------+
| requestor_id           | `Description`    | ID of user requesting the job (helpful for grouping)                 |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Allowed Values` | String                                                               |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Example`        | `requestor_id=sample_id`                                             |
+------------------------+------------------+----------------------------------------------------------------------+
| callback_url           | .. raw:: html                                                                           |
|                        |                                                                                         |
|                        |  A URL with query string which will be called on completion.</br>                       |
|                        |  If submitting the <i>callback_url</i> as a query string parameter, rather than</br>    |
|                        |  a value in the POST data, the <i>callback_url</i> should be URL encoded.</br>          |
|                        |  The callback URL can contain tags that will be replaced with</br>                      |
|                        |  job specific data when the callback is called.</br>                                    |
|                        |  Below is the list of tags that are supported:</br>                                     |
|                        |  &nbsp;&nbsp;<b>{job_id}</b> The job UUID</br>                                          |
|                        |  &nbsp;&nbsp;<b>{job_name}</b> The job name</br>                                        |
|                        |  &nbsp;&nbsp;<b>{elementlist_version}</b> The ElementList version</br>                  |
|                        |  &nbsp;&nbsp;<b>{iwp_name}</b> The Interim Work Product name associated with this</br>  |
|                        |  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ElementList version</br>   |
|                        |                                                                                         |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Allowed Values` | URL Encoded String                                                   |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Example`        | ``callback_url=http%3A%2F%2Fdomain.com%2Fpath``                      |
+------------------------+------------------+----------------------------------------------------------------------+
| expected_speakers      | `Description`    | Amount of speakers that the video will have                          |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Allowed Values` | Integer                                                              |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Example`        | ``expected_speakers=40``                                             |
+------------------------+------------------+----------------------------------------------------------------------+
| notes                  | `Description`    | Terms, Names, etc. to aid in human transcription                     |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Allowed Values` | String                                                               |
|                        +------------------+----------------------------------------------------------------------+
|                        | `Example`        | ``Interviewee is Dee``                                               |
+------------------------+------------------+----------------------------------------------------------------------+

**Responses**

+-----------+------------------------------------------------------------------------------------------+
| HTTP Code | Details                                                                                  |
+===========+===============+==========================================================================+
| 204       | `Description` | Success                                                                  |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | none                                                                     |
+-----------+---------------+--------------------------------------------------------------------------+
| 400       | `Description` | An error occurred                                                        |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | Error description (see :ref:`error-format-label` for details)            |
+-----------+---------------+--------------------------------------------------------------------------+

**Example Requests**

.. sourcecode:: http

    POST /api/job/modify HTTP/1.1
    Host: api.cielo24.com
    Body: v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f
          &job_id=64bea283eff6475ea6596027a6ba0929
          &transcription_fidelity=PREMIUM&priority=STANDARD&account_id=john_doe

**Example Response**

.. sourcecode:: http

    HTTP/1.1 204 OK
