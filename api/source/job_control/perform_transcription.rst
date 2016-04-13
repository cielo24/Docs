Perform Transcription
=====================

Request that transcription be performed on the specified job.
A callback URL, if specified, will be called when the transcription is complete.
See :ref:`callback documentation <callbacks-label>` for details.

**HTTP Method**

.. http:get:: /api/job/perform_transcription

**Query String Parameters** — Required

+------------------------+-------------------------------------------------------------------------------------+
| Name                   | Details                                                                             |
+========================+==================+==================================================================+
| v                      | `Description`    | The version of the API to use                                    |
|                        +------------------+------------------------------------------------------------------+
|                        | `Allowed Values` | 1                                                                |
|                        +------------------+------------------------------------------------------------------+
|                        | `Example`        | ``v=1``                                                          |
+------------------------+------------------+------------------------------------------------------------------+
| api_token              | `Description`    | The API token used for this session                              |
|                        +------------------+------------------------------------------------------------------+
|                        | `Allowed Values` | Hex String                                                       |
|                        +------------------+------------------------------------------------------------------+
|                        | `Example`        | ``api_token=7ca5dc5c7cce449fb0fff719307e8f5f``                   |
+------------------------+------------------+------------------------------------------------------------------+
| job_id                 | `Description`    | The ID of the job                                                |
|                        +------------------+------------------------------------------------------------------+
|                        | `Allowed Values` | Hex String                                                       |
|                        +------------------+------------------------------------------------------------------+
|                        | `Example`        | ``job_id=64bea283eff6475ea6596027a6ba0929``                      |
+------------------------+------------------+------------------------------------------------------------------+
| transcription_fidelity | `Description`    | The desired fidelity of the transcription                        |
|                        +------------------+------------------------------------------------------------------+
|                        | `Allowed Values` | :ref:`fidelity-label`                                            |
|                        +------------------+------------------------------------------------------------------+
|                        | `Example`        | ``transcription_fidelity=PREMIUM``                               |
+------------------------+------------------+------------------------------------------------------------------+
| priority               | .. raw:: html                                                                       |
|                        |                                                                                     |
|                        |  The desired priority of the transcription.                                         |
|                        |                                                                                     |
|                        +------------------+------------------------------------------------------------------+
|                        | `Allowed Values` | :ref:`priority-label`                                            |
|                        +------------------+------------------------------------------------------------------+
|                        | `Example`        | ``priority=STANDARD``                                            |
+------------------------+------------------+------------------------------------------------------------------+

**Query String Parameters** — Optional

+-------------------------+-----------------------------------------------------------------------------------------+
| Name                    | Details                                                                                 |
+=========================+=========================================================================================+
| callback_url            | .. raw:: html                                                                           |
|                         |                                                                                         |
|                         |  A URL with query string which will be called on completion.</br>                       |
|                         |  If submitting the <i>callback_url</i> as a query string parameter, rather than</br>    |
|                         |  a value in the POST data, the <i>callback_url</i> should be URL encoded.</br>          |
|                         |  The callback URL can contain tags that will be replaced with</br>                      |
|                         |  job specific data when the callback is called.</br>                                    |
|                         |  Below is the list of tags that are supported:</br>                                     |
|                         |  &nbsp;&nbsp;<b>{job_id}</b> The job UUID</br>                                          |
|                         |  &nbsp;&nbsp;<b>{job_name}</b> The job name</br>                                        |
|                         |  &nbsp;&nbsp;<b>{elementlist_version}</b> The ElementList version</br>                  |
|                         |  &nbsp;&nbsp;<b>{iwp_name}</b> The Interim Work Product name associated with this</br>  |
|                         |  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ElementList version</br>   |
|                         |                                                                                         |
|                         +------------------+----------------------------------------------------------------------+
|                         | `Allowed Values` | URL Encoded String                                                   |
|                         +------------------+----------------------------------------------------------------------+
|                         | `Example`        | ``callback_url=http%3A%2F%2Fdomain.com%2Fpath``                      |
+-------------------------+------------------+----------------------------------------------------------------------+
| options                 | .. raw:: html                                                                           |
|                         |                                                                                         |
|                         |  A job options dictionary. See next section for details.                                |
|                         |                                                                                         |
|                         +------------------+----------------------------------------------------------------------+
|                         | `Allowed Values` | Stringified dictionary                                               |
|                         +------------------+----------------------------------------------------------------------+
|                         | `Example`        | ``options={"notes":"test","speaker_id":true}``                       |
+-------------------------+------------------+----------------------------------------------------------------------+
| target_language         | .. raw:: html                                                                           |
|                         |                                                                                         |
|                         |  A language code or a comma separated language codes list to translate </br>            |
|                         |  this job into.</br>                                                                    |
|                         |  If not specified, then no translation will be performed.</br>                          |
|                         |  If specified, but the language code specified matches the language</br>                |
|                         |  code on the job request, then no translation will be performed.</br>                   |
|                         |                                                                                         |
|                         +------------------+----------------------------------------------------------------------+
|                         | `Allowed Values` | See :ref:`languages-label` (comma separated for multiple)            |
|                         +------------------+----------------------------------------------------------------------+
|                         | `Example`        | ``target_language=de,fr,it``                                         |
+-------------------------+------------------+----------------------------------------------------------------------+
| turnaround_hours        | .. raw:: html                                                                           |
|                         |                                                                                         |
|                         |  The number of hours after submission that the job will be returned.</br>               |
|                         |  If not specified, it will be set to a default based on the value of</br>               |
|                         |  the priority parameter. The defaults are 24 and 48 for the</br>                        |
|                         |  PRIORITY and STANDARD priorities respectively. If you</br>                             |
|                         |  request a smaller number of hours than the default for the</br>                        |
|                         |  priority you have selected, the priority will be automatically</br>                    |
|                         |  changed. For example if you request a <i>turnaround_hours</i> of 16</br>               |
|                         |  with a priority of STANDARD, the priority will be automatically,</br>                  |
|                         |  and silently, changed to PRIORITY.                                                     |
|                         +------------------+----------------------------------------------------------------------+
|                         | `Allowed Values` | Integer                                                              |
|                         +------------------+----------------------------------------------------------------------+
|                         | `Example`        | ``turnaround_hours=36``                                              |
+-------------------------+------------------+----------------------------------------------------------------------+
| standard_product        | .. raw:: html                                                                           |
|                         |                                                                                         |
|                         |  Flag to determine whether the media is sent through </br>                              |
|                         |  the standard product or the legacy product                                             |
|                         +------------------+----------------------------------------------------------------------+
|                         | `Allowed Values` | URL Encoded String: true, false, y, n, t, f                          |
|                         +------------------+----------------------------------------------------------------------+
|                         | `Example`        | ``standard_product=true``                                            |
+-------------------------+------------------+----------------------------------------------------------------------+

**Job Options**
  | The following options can be provided as a stringified dictionary.
  | The resulting string will be the value of the `options` query parameter.
  | Example: ``options={"notes":"test_note","speaker_id":true}``

+---------------------------------+-----------------------------------------------------------------------------------------+
| Name                            | Details                                                                                 |
+=================================+=========================================================================================+
| customer_approval_steps         | .. raw:: html                                                                           |
|                                 |                                                                                         |
|                                 |  Requires your approval of a job at specified points in the</br>                        |
|                                 |  workflow. When the job is ready for approval you will be emailed</br>                  |
|                                 |  a link that will take you to a web based tool you can use to view,</br>                |
|                                 |  edit and approve the job. You may request approval at two points<br>                   |
|                                 |  in the workflow: before translation and before the job is returned.                    |
|                                 |                                                                                         |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Allowed Values` | [ TRANSLATION, RETURN ]                                              |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Default Value`  | []                                                                   |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Example`        | ``customer_approval_steps=[TRANSLATION]``                            |
+---------------------------------+------------------+----------------------------------------------------------------------+
| customer_approval_tool          | .. raw:: html                                                                           |
|                                 |                                                                                         |
|                                 |  Determines which web based tool to use for viewing, editing</br>                       |
|                                 |  and approving jobs.                                                                    |
|                                 |                                                                                         |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Allowed Values` | [ AMARA, CIELO24 ]                                                   |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Default Value`  | CIELO24                                                              |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Example`        | ``customer_approval_tool=CIELO24``                                   |
+---------------------------------+------------------+----------------------------------------------------------------------+
| custom_metadata                 | .. raw:: html                                                                           |
|                                 |                                                                                         |
|                                 |  A JSON dictionary of key value pairs. These will be used</br>                          |
|                                 |  as substitution strings when building the callback URL and</br>                        |
|                                 |  custom DFXP caption header.                                                            |
|                                 |                                                                                         |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Allowed Values` | Single level JSON dictionary                                         |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Default Value`  | {}                                                                   |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Example`        | ``custom_metadata={"key":"value"}``                                  |
+---------------------------------+------------------+----------------------------------------------------------------------+
| notes                           | .. raw:: html                                                                           |
|                                 |                                                                                         |
|                                 |  Allows you to provide text that will be displayed to</br>                              |
|                                 |  the transcriber when the job is processed.</br>                                        |
|                                 |  An HTML included will be escaped.                                                      |
|                                 |                                                                                         |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Allowed Values` | String ( <= 1000 characters)                                         |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Default Value`  | ""                                                                   |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Example`        | ``notes=sometext``                                                   |
+---------------------------------+------------------+----------------------------------------------------------------------+
| return_iwp                      | .. raw:: html                                                                           |
|                                 |                                                                                         |
|                                 |  Allows you to receive additional callbacks when interim</br>                           |
|                                 |  versions of the job are completed. If you specified a</br>                             |
|                                 |  <i>callback_url</i>, then a callback will sent for FINAL</br>                          |
|                                 |  regardless of the value of this option.                                                |
|                                 |                                                                                         |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Allowed Values` | :ref:`iwp-label`                                                     |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Default Value`  | []                                                                   |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Example`        | ``return_iwp=[MECHANICAL,FINAL]``                                    |
+---------------------------------+------------------+----------------------------------------------------------------------+
| speaker_id                      | .. raw:: html                                                                           |
|                                 |                                                                                         |
|                                 |  Requests that speaker names be identified.                                             |
|                                 |                                                                                         |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                              |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Default Value`  | false                                                                |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Example`        | ``speaker_id=true``                                                  |
+---------------------------------+------------------+----------------------------------------------------------------------+
| enable_true_verbatim            | .. raw:: html                                                                           |
|                                 |                                                                                         |
|                                 |  Requests True Verbatim workflow.                                                       |
|                                 |                                                                                         |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                              |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Default Value`  | false                                                                |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Example`        | ``enable_true_verbatim=true``                                        |
+---------------------------------+------------------+----------------------------------------------------------------------+
| first_pass_campaign             | .. raw:: html                                                                           |
|                                 |                                                                                         |
|                                 |  Requests Specific First Pass Campaign.                                                 |
|                                 |                                                                                         |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Allowed Values` | [NORMAL, GENERAL_CONTENT, TRUE_VERBATIM]                             |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Default Value`  | NORMAL                                                               |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Example`        | ``first_pass_campaign=TRUE_VERBATIM``                                |
+---------------------------------+-------+----------+----------------------------------------------------------------------+
| generate_media_intelligence_iwp | .. raw:: html                                                                   |
|                                 |                                                                                 |
|                                 |  Requests that media intelligence be generated for the specified </br>          |
|                                 |  interim/final versions of the transcript. Media intelligence data is</br>      |
|                                 |  added to the ElementList and can be retrieve using the</br>                    |
|                                 |  <i>get_elementlist</i> API call.</br>                                          |
|                                 |                                                                                 |
|                                 | .. container::                                                                  |
|                                 |                                                                                 |
|                                 |    See :ref:`ElementList <media-intelligence-label>` for details.               |
|                                 |                                                                                 |
|                                 +------------------+--------------------------------------------------------------+
|                                 | `Allowed Values` | :ref:`iwp-label`                                             |
|                                 +------------------+--------------------------------------------------------------+
|                                 | `Default Value`  | []                                                           |
|                                 +------------------+--------------------------------------------------------------+
|                                 | `Example`        | ``generate_media_intelligence_iwp=[MECHANICAL,FINAL]``       |
+---------------------------------+------------------+----------------------------------------------------------------------+
| audio_description               | .. raw:: html                                                                           |
|                                 |                                                                                         |
|                                 |  Requests that all noises and sounds be identified.                                     |
|                                 |                                                                                         |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                              |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Default Value`  | false                                                                |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Example`        | ``audio_description=true``                                           |
+---------------------------------+------------------+----------------------------------------------------------------------+
| on_screen_text                  | .. raw:: html                                                                           |
|                                 |                                                                                         |
|                                 |  Requests that any text that appears in the media be added to the transcription.        |
|                                 |                                                                                         |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                              |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Default Value`  | false                                                                |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Example`        | ``on_screen_text=true``                                              |
+---------------------------------+------------------+----------------------------------------------------------------------+
| music_lyrics                    | .. raw:: html                                                                           |
|                                 |                                                                                         |
|                                 |  Requests that lyrics to songs be transcribed instead of labeled [MUSIC].               |
|                                 |                                                                                         |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                              |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Default Value`  | false                                                                |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Example`        | ``music_lyrics=true``                                                |
+---------------------------------+------------------+----------------------------------------------------------------------+
| custom_special_handling         | .. raw:: html                                                                           |
|                                 |                                                                                         |
|                                 |  Requests that transcribers follow submitted instruction set.                           |
|                                 |                                                                                         |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                              |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Default Value`  | false                                                                |
|                                 +------------------+----------------------------------------------------------------------+
|                                 | `Example`        | ``custom_special_handling=true``                                     |
+---------------------------------+------------------+----------------------------------------------------------------------+


**Responses**

+-----------+------------------------------------------------------------------------------------------+
| HTTP Code | Details                                                                                  |
+===========+===============+==========================================================================+
| 200       | `Description` | Success                                                                  |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | .. code-block:: javascript                                               |
|           |               |                                                                          |
|           |               |  {                                                                       |
|           |               |    "TaskId" : "Encoded Task ID"                                          |
|           |               |  }                                                                       |
+-----------+---------------+--------------------------------------------------------------------------+
| 400       | `Description` | An error occurred                                                        |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | Error description (see :ref:`error-format-label` for details)            |
+-----------+---------------+--------------------------------------------------------------------------+

**Example Requests**

.. sourcecode:: http

    GET /api/job/perform_transcription?v=1
    &api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &job_id=64bea283eff6475ea6596027a6ba0929
    &transcription_fidelity=PREMIUM&priority=STANDARD HTTP/1.1
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    { "TaskId" : "41ec7d23fb4b45f9b48a13d0b7283bf2" }
