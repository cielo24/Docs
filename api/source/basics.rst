The Basics
==========

Getting Started
---------------
#. Send an email to `support@cielo24.com <mailto:support@cielo24.com>`_ requesting a sandbox API login.
#. Download sample API code from our repo: https://github.com/Cielo24/SampleCode

    #. Each sample code project includes a command line application you can use to experiment with the API without writing any code of your own.

#. Use the sandbox credentials you received from support and the sample applications to connect to our API

Sandbox API
-----------
For testing, a sandbox API is provided at https://sandbox.cielo24.com.
The sandbox provides a testing platform for development, where no real processing is performed.
Transcript/caption requests made to the sandbox will return a pre-prepared sample, the data will not match the content or length of media you submitted.
However, the transcript/caption will be formatted as you request in your get_transcription/get_caption call.
The sandbox API will make URL callbacks, if requested, a few seconds after the call to perform_transcription is made.

Production API
--------------
The production API can be accessed from the following location: https://api.cielo24.com.

Account Management
------------------

Account management is largely performed outside of the API. To set up a new production account please register for an account at http://www.cielo24.com. To request a sandbox account, email to `support@cielo24.com <mailto:support@cielo24.com>`_.

Sub-Accounts
------------

The cielo24 API supports sub-account creation.
For organizational and access control purposes, you may create an account that is a sub-account to a primary account.
The primary account will have the ability to generate a securekey for a subaccount, and thereby login and access it as normal without requiring knowledge of the password.

Each sub-account is a full normal account with its own list of jobs and media.
Different sub accounts cannot access the data for each other, so this is a good way to compartmentalize your data while still being under the header of a single parent account.

Sub-accounts can, in turn, create their own further sub-accounts. In all cases, a primary account has access to its subs, and its subs’ subs, and so on.

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

Transcription and translation are supported in the following languages:

+---------------------+--------------------+
| Language            | IEFT Language Code |
+=====================+====================+
| Arabic              | ar                 |
+---------------------+--------------------+
| English             | en                 |
+---------------------+--------------------+
| French              | fr                 |
+---------------------+--------------------+
| German              | de                 |
+---------------------+--------------------+
| Hebrew              | he                 |
+---------------------+--------------------+
| Hindi               | hi                 |
+---------------------+--------------------+
| Italian             | it                 |
+---------------------+--------------------+
| Japanese            | jp                 |
+---------------------+--------------------+
| Korean              | ko                 |
+---------------------+--------------------+
| Mandarin Chinese    | cmn                |
+---------------------+--------------------+
| Portuguese          | pt                 |
+---------------------+--------------------+
| Russian             | ru                 |
+---------------------+--------------------+
| Spanish             | es                 |
+---------------------+--------------------+
| Traditional Chinese | zh                 |
+---------------------+--------------------+
| Turkish             | tr                 |
+---------------------+--------------------+