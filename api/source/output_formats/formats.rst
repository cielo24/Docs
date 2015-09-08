JSON Formats
============

Below are the descriptions of the formats used in cielo24 API.

.. _job-info-format-label:

Job Info Format
---------------

The following defines the Job Info in JSON format:

.. code-block:: javascript

    {
        "JobId" : "<Guid HexString>",
        "JobName" : "<String>",
        "MediaLengthSeconds" : "<Float>",
        "ExternalID" : "<String (dependant on third-party integrations)",
        "Priority" : "<Priority Enum>",
        "Fidelity" : "<Fidelity Enum>",
        "JobStatus" : "<Status Enum>",
        "Options" : {
            "<JobConfigOption>" : "<Value>"
            ...
        },
        "ReturnTargets" : {
            "<ReturnTargetName>" : "<ReturnTargetValue>",
            ...
        },
        "SourceLanguage" : "<RFC 5646 Language Code>",
        "TargetLanguage" : "<RFC 5646 Language Code>",
        "CreationDate" : "<ISO 8601 Date String>",
        "StartDate" : "<ISO 8601 Date String>",
        "DueDate" : "<ISO 8601 Date String>",
        "CompletedDate" : "<ISO 8601 Date String>",
        "ReturnDate": "<ISO 8601 Date String>",
        "AuthorizationDate": "<ISO 8601 Date String>",
        "JobDifficulty" : "<JobDifficulty Enum>"
    }

.. container::

    Related: :ref:`priority-label`,
    :ref:`fidelity-label`,
    :ref:`job-status-label`,
    :ref:`job-difficulty-label`
    .

.. raw:: html

    </br>

.. _job-list-format-label:

Job List Format
---------------

The following defines the Job List in JSON format:

.. code-block:: javascript

    {
        "Username" : "<String>",
        "ActiveJobs" :
        [
            "List of Jobs (see below)"
        ]
    }

.. _job-format-label:

Job Format
----------

The following defines the Job in JSON format:

.. code-block:: javascript

    {
        "JobId" : "<Guid HexString>",
        "JobName" : "<String>",
        "Username": "<String>",
        "MediaLengthSeconds" : "<Float>",
        "ExternalID" : "<String (dependant on third-party integrations)",
        "Priority" : "<Priority Enum>",
        "Fidelity" : "<Fidelity Enum>",
        "JobStatus" : "<Status Enum>",
        "SourceLanguage" : "<RFC 5646 Language Code>",
        "TargetLanguage" : "<RFC 5646 Language Code>",
        "CreationDate" : "<ISO 8601 Date String>",
        "StartDate" : "<ISO 8601 Date String>",
        "DueDate" : "<ISO 8601 Date String>",
        "CompletedDate" : "<ISO 8601 Date String>",
        "ReturnDate": "<ISO 8601 Date String>",
        "AuthorizationDate": "<ISO 8601 Date String>",
        "JobDifficulty": "<JobDifficulty Enum>",
        "Options" : {
            "<JobConfigOption>" : "<Value>"
            ...
        },
        "ReturnTargets" : {
            "<ReturnTargetName>" : "<ReturnTargetValue>",
            ...
        }
    }

.. container::

    Related: :ref:`job-status-label`,
    :ref:`fidelity-label`,
    :ref:`priority-label`,
    :ref:`job-difficulty-label`
    .

.. raw:: html

    </br>

.. _error-format-label:

Error Format
------------

The following defines the Error Output in JSON format:

.. code-block:: javascript

    {
        "ErrorType" : "<ErrorType Enum>",
        "ErrorComment" : "<String>"
    }

.. container::

    Related: :ref:`error-type-label`.

.. raw:: html

    </br>

.. _elementlist-list-format-label:

ElementList List Format
-----------------------

The following defines the ElementList list in JSON format:

.. code-block:: javascript

    [{
        "iwp_name" : "<String>",
        "version" : "<ISO 8601 Date String>"
    }]