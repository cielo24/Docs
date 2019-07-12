Add Custom Guideline To Job
===========================

Add a set of guidelines for transcribers to follow when transcribing the media.

To add guidelines from a publicly accessible URL where the guidelines is the actual web page,
make a GET request and specify the URL in the **guidelines_url** parameter and specify **is_html** parameter as **true**.

To add guidelines from a publicly accessible Download URL,
make a GET request and specify the URL in the **guidelines_url** parameter.
(you do not need to specify **is_html** as false)

To add media rom a local file, make a POST request,
Do NOT specify the **guidelines_url** parameter in the request URL.
The media should be uploaded with a multipart/form content type where the file is uploaded to form-field input **file**

**Note**
if you upload a custom guidelines set, when you call the **perform_transcription** api endpoint,
you must call the option parameter with **custom_special_handling** set to **true**


**HTTP Method**

.. http:get:: /api/job/add_custom_guidelines (from URL)

.. http:post:: /api/job/add_custom_guidelines (from local file)

**Query String Parameters** - Required (always)

+------------------+-------------------------------------------------------------------------------------------+
| Name             | Details                                                                                   |
+==================+==================+========================================================================+
| api_token        | `Description`    | The API token used for this session                                    |
|                  +------------------+------------------------------------------------------------------------+
|                  | `Allowed Values` | Hex String                                                             |
|                  +------------------+------------------------------------------------------------------------+
|                  | `Example`        | ``api_token=7ca5dc5c7cce449fb0fff719307e8f5f``                         |
+------------------+-------------------------------------------------------------------------------------------+
| job_id           | `Description`    | The API token used for this session                                    |
|                  +------------------+------------------------------------------------------------------------+
|                  | `Allowed Values` | Hex String                                                             |
|                  +------------------+------------------------------------------------------------------------+
|                  | `Example`        | ``job_id=64bea283eff6475ea6596027a6ba0929``                            |
+------------------+-------------------------------------------------------------------------------------------+


**Query String Parameters** -- Required `(when adding guidelines from URL)`

+------------------+-------------------------------------------------------------------------------------------+
| Name             | Details                                                                                   |
+==================+==================+========================================================================+
| guidelines_url   | `Description`    | The URL from which custom_guidelines will be obtained                  |
|                  +------------------+------------------------------------------------------------------------+
|                  | `Allowed Values` | URL Encoded String                                                     |
|                  +------------------+------------------------------------------------------------------------+
|                  | `Example`        | ``guidelines_url=https://cielo24.com/guidelines/``                     |
+------------------+------------------+------------------------------------------------------------------------+

**Query String Parameters** -- Required `(when adding guidelines from URL where the web page is the guidelines)`

+------------------+-------------------------------------------------------------------------------------------+
| Name             | Details                                                                                   |
+==================+==================+========================================================================+
| is_html          | `Description`    | flag to indicate whether url is download or webpage                    |
|                  +------------------+------------------------------------------------------------------------+
|                  | `Allowed Values` | `true` or `false`                                                      |
|                  +------------------+------------------------------------------------------------------------+
|                  | `Example`        | ``is_html=true``                                                       |
+------------------+------------------+------------------------------------------------------------------------+

**Request Body** — Required `(when adding guidelines from local file)`

+------------------+-------------------------------------------------------------------------------------------+
| Name             | Details                                                                                   |
+==================+==================+========================================================================+
| file             | `Description`    | Raw binary of a .txt file                                              |
|                  +------------------+------------------------------------------------------------------------+
|                  | `Allowed Values` | not applicable                                                         |
|                  +------------------+------------------------------------------------------------------------+
|                  | `Example`        | ``Content-Disposition: form-data; name="file"; filename="file1.txt"``  |
|                  |                  | ``Content-Type: text/plain``                                           |
+------------------+------------------+------------------------------------------------------------------------+

**Example Requests**

.. sourcecode:: http

    GET /api/job/add_custom_guidelines?api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &job_id=64bea283eff6475ea6596027a6ba0929
    &guidelines_url=https%3A%2F%2Fcielo24.com%2Fguidelines%2F
    &is_html=true HTTP/1.1

.. sourcecode:: http

    POST /api/job/add_custom_guidelines?api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &job_id=64bea283eff6475ea6596027a6ba0929 HTTP/1.1
    Content-Length: 1037
    Expect: 100-continue
    Content-Type: multipart/form-data; boundary=------------------------d74496d66958873e
    Content-Disposition: form-data; name="file"; filename="file.txt"
    Content-Type: text/plain

    contents of the file here
    --------------------------d74496d66958873e--

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    {"CUSTOM_GUIDELINES_STORED": {"full_html": false, "storage_data": {"path": "public/original-media/5523e8c8d34444c38e675e1f46f2b55c.txt", "account": "1eff263d871f460f86f5a4d133a7e727", "bucket": "cielo24-dev-dev-main-storage", "size": 1037}}}
