The Basics
==========

Interface Access & Sandbox
--------------------------

The API can be accessed from the following location: https://api.cielo24.com. For testing, a sandbox is provided at https://sandbox.cielo24.com. The sandbox provides a testing platform for development, where no real processing is performed, and all results are for use in evaluating compliance with the interface. The API returns a canned transcript sample for all requests. All requested transcript and caption formats are derived from this pre-transcribed content.

.. note:: In the the sandbox, some transcript and caption formats will not necessarily reflect the exact manipulations requested through the API. For example, the number of caption lines and characters per caption line are fixed.

Account Management
------------------
Account management is largely performed outside of the API. To set up a new account please register for an account at http://www.cielo24.com.

Sub-Accounts
------------

The cielo24 API supports sub-account creation. For organizational and access control purposes, you may create an account that is a sub-account to a primary account. The primary account will have the ability to generate a securekey for a subaccount, and thereby login and access it as normal without requiring knowledge of the password.
Each sub-account is a full normal account with its own list of jobs and media. Different sub accounts cannot access the data for each other, so this is a good way to compartmentalize your data while still being under the header of a single parent account.
Sub-accounts can, in turn, create their own further sub-accounts. In all cases, a primary account has access to its subs, and its subs’ subs, and so on.

Callbacks
---------

Many processing requests such as transcription and synchronization are not completed immediately. As such, the interface supports the use of a callback URL that is provided by the application developer. Once the job has completed, the API calls this callback URL to inform the application that the specific job has been completed. We make an HTTP GET request to the callback URL. HTTPS URLs are supported as well. We will not retry the callback if there is a failure on the remote (your) side. We do not send any additional data with the callback,. You may wish to include a unique identifier in the URL so you can tell which request has completed. For example:
http://www .yourdomain.com/cielo24/request_complete?job_id=1234

Polling
------
If a callback URL is not practical, the application can poll the interface by requesting the status of a given task that is associated with a given job. The task status will indicate COMPLETE when the task is done.