The Basics
==========

Getting Started
---------------
#. Send an email to `support@cielo24.com <mailto:support@cielo24.com>`_ requesting a sandbox API login.

#. Download our API libraries: `Python <https://github.com/Cielo24/cielo24-python>`_, `Ruby <https://github.com/Cielo24/cielo24-ruby>`_, `Java <https://github.com/Cielo24/cielo24-java>`_, `PHP <https://github.com/Cielo24/cielo24-php>`_, `.NET <https://github.com/Cielo24/cielo24-dotnet>`_.

    #. Each project includes a core library and a command line application you can use to experiment with the API without writing any code of your own.

#. Use the sandbox credentials you received from support and the libraries to connect to our API.

Sandbox API
-----------
For testing, a sandbox API is provided at https://sandbox.cielo24.com.
The sandbox provides a testing platform for development, where no real processing is performed.
Transcript/caption requests made to the sandbox will return a pre-prepared sample, the data will not match the content or length of media you submitted.
However, the transcript/caption will be formatted as you request in your :doc:`get_transcript <job_control/get_transcript>` **/** :doc:`get_caption <job_control/get_caption>` call.
The sandbox API will make URL callbacks, if requested, a few seconds after the call to :doc:`perform_transcription <job_control/perform_transcription>` is made.

Production API
--------------
The production API can be accessed from the following location: https://api.cielo24.com.

Account Management
------------------

Account management is largely performed outside of the API. To set up a new production account please register for an account at http://www.cielo24.com.
To request a sandbox account, email to `support@cielo24.com <mailto:support@cielo24.com>`_.

Sub-Accounts
------------

Upon request, multiple accounts may be created for you to control access or simplify billing.
These accounts will be related to one another by parent-child relationships.
An unlimited number of relationship levels may be created, i.e. parent, child, grandchild.

Each sub-account is a normal account with its own list of jobs and media.
Access is restricted to the jobs in an account and that account's descendants.
For example, the credentials for a child account may be used to create and/or access jobs in a grandchild account, but not in a parent or sibling accounts.

For the most part, the access to the jobs of sub-accounts is transparent, as most API calls operate using a job ID.
Simply login as a parent, and access jobs of the sub-account as if they belonged to the parent.
However, for some API calls, such as Create Job and List Jobs, you will need to pass an additional
parameter to specify the sub account you want to use.

If you are interested in using sub-accounts, please contact support@cielo24.com for more information.

.. _callbacks-label:

Callbacks
---------

Processing requests such as transcription are not completed immediately.
As such, the interface supports the use of a callback URL that is provided by the application developer.
Once the job has completed, the API calls this callback URL to inform the application that the specific job has been completed.
We make a GET request to the callback URL. HTTPS and embedded basic HTTP auth URLs are supported.
We will retry callbacks three times over a 30 minute period if the remote server doesn't return a HTTP success code (200 OK.)
You may wish to include a unique identifier in the URL so you can tell which request has completed, or you can request that we send additional data with the callback.
See the callback_url parameter of each method for a list of the data that can be sent.

For example: http://www.yourdomain.com/cielo24/request_complete?job_id=1234

Polling
-------

If a callback URL is not practical, the application can poll the interface by requesting the status of a given task that is associated with a given job. The task status will indicate COMPLETE when the task is done.

Languages
---------

We support transcription to and from any of the following languages. However, please note that if English is not a source or target language, an additional translation will incur as we will have to generate a translation from the source language into English and then from English into the Target language. This will result in increased charges.

Transcription and translation are supported in the following languages for PROFESSIONAL fidelity jobs:

+-------------------------------------+--------------------+
| Language                            | IETF Language Code |
+=====================================+====================+
| Arabic                              | ar                 |
+-------------------------------------+--------------------+
| Chinese - Mandarin (Traditional)    | zh-tw              |
+-------------------------------------+--------------------+
| Chinese - Mandarin (Simplified)     | zh-cmn             |
+-------------------------------------+--------------------+
| Chinese - Cantonese (Traditional)   | zh-yue             |
+-------------------------------------+--------------------+
| Dutch                               | nl                 |
+-------------------------------------+--------------------+
| English                             | en                 |
+-------------------------------------+--------------------+
| French                              | fr                 |
+-------------------------------------+--------------------+
| German                              | de                 |
+-------------------------------------+--------------------+
| Hebrew                              | he                 |
+-------------------------------------+--------------------+
| Hindi                               | hi                 |
+-------------------------------------+--------------------+
| Italian                             | it                 |
+-------------------------------------+--------------------+
| Japanese                            | ja                 |
+-------------------------------------+--------------------+
| Korean                              | ko                 |
+-------------------------------------+--------------------+
| Portuguese                          | pt                 |
+-------------------------------------+--------------------+
| Russian                             | ru                 |
+-------------------------------------+--------------------+
| Spanish                             | es                 |
+-------------------------------------+--------------------+
| Turkish                             | tr                 |
+-------------------------------------+--------------------+

Transcription is supported in the following languages for MECHANICAL fidelity jobs:

+---------------------+--------------------+
| Language            | IETF Language Code |
+=====================+====================+
| Dutch               | nl                 |
+---------------------+--------------------+
| English             | en                 |
+---------------------+--------------------+
| French              | fr                 |
+---------------------+--------------------+
| German              | de                 |
+---------------------+--------------------+
| Italian             | it                 |
+---------------------+--------------------+
| Spanish             | es                 |
+---------------------+--------------------+
| Portuguese          | pt                 |
+---------------------+--------------------+
