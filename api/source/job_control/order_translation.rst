Order Translation
=================

Request that orders a Translation job for a previously completed Job.
The New Job ID and job target language will be returned upon completion.

**HTTP Method**

.. http:get:: /api/job/translate

**Query String Parameters** - Required

+------------------------+-------------------------------------------------------------------------------------+
| Name                   | Details                                                                             |
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
| target_languages       | `Description`    | The language(s) being ordered                                    |
|                        +------------------+------------------------------------------------------------------+
|                        | `Allowed Values` | URL Encoded String (see allowed languages for language code)     |
|                        +------------------+------------------------------------------------------------------+
|                        | `Example`        | ``target_languages=fr%2Cde``                                     |
+------------------------+------------------+------------------------------------------------------------------+

**Query String Parameters** - Optional

+-------------------------+-----------------------------------------------------------------------------------------+
| Name                    | Details                                                                                 |
+=========================+=========================================================================================+
| approve_uplevel         | .. raw:: html                                                                           |
|                         |                                                                                         |
|                         | Mechanical Jobs must be upleveled before a Translation can be ordered. If ordering      |
|                         | a translation on a Mechanical job this parameter becomes required.                      |
|                         +------------------+----------------------------------------------------------------------+
|                         | `Allowed Values` | "yes"                                                                |
|                         +------------------+----------------------------------------------------------------------+
|                         | `Example`        | ``approve_uplevel=yes``                                              |
+-------------------------+------------------+----------------------------------------------------------------------+

**Example Requests**

.. sourcecode:: http

    GET /api/job/perform_transcription?v=1
    &api_token=28beb5ecb23f498ea2e71efa49e0fd10
    &job_id=f5b0a29c28804326ac6840863dfde14b
    &target_languages=fr%2Cde
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 201 CREATED
    Content-Type: application/json

    {"translation_job_ids": [["91aa19d058aa42b1ac98339a24a36503", "Child Translation Created for fr"], ["f51dc35a39114b4c9c8c874b422e819e", "Child Translation Created for de"]], "translation_language": "fr,de"}
