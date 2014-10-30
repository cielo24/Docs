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
        "MediaLengthSeconds" : "<Integer>",
        "ExternalID" : "<String (dependant on third-party integrations)",
        "Priority" : "<Priority Enum>",
        "TurnaroundTimeHours" : "<Integer>",
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
        "Language" : "<RFC 5646 Language Code>",
        "SourceLanguage" : "<RFC 5646 Language Code>",
        "TargetLanguage" : "<RFC 5646 Language Code>",
        "CreationDate" : "<ISO 8601 Date String>",
        "StartDate" : "<ISO 8601 Date String>",
        "DueDate" : "<ISO 8601 Date String>",
        "CompletedDate" : "<ISO 8601 Date String>",
        "Tasks" :
        [
            "List of Task Statuses (see below)"
        ]
    }

.. _task-status-format-label:

Task Status Format
------------------

The following defines the Task Status in JSON format:

.. code-block:: javascript

    {
        "TaskId" : "<Guid HexString>",
        "TaskType" : "<TaskType Enum>",
        "TaskRequestTime" : "<ISO 8601 Date String>",
        "TaskCompletionTime" : "<ISO 8601 Date String>",
        "TaskInfo" : "<String (additional information defined on a per-task basis)>",
        "TaskStatus" : "<TaskStatus Enum>",
    }

.. container::

    Related: :ref:`task-status-label`,
    :ref:`task-type-label`
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
        "MediaLengthSeconds" : "<Integer>",
        "ExternalID" : "<String (dependant on third-party integrations)",
        "JobStatus" : "<Status Enum>",
        "Priority" : "<Priority Enum>",
        "Fidelity" : "<Fidelity Enum>",
        "JobLanguage" : "<RFC 5646 Language Code>",
        "TargetLanguage" : "<RFC 5646 Language Code>",
        "CreationTime" : "<ISO 8601 Date String>",
        "DueDate" : "<ISO 8601 Date String>",
        "TurnaroundTimeHours" : "<Integer>",
        "StartTime" : "<ISO 8601 Date String>",
        "CompletedTime" : "<ISO 8601 Date String>"
        "Options" : {
            "<JobConfigOption>" : "<Value>"
            ...
        },
        "ReturnTargets" : {
            "<ReturnTargetName>" : "<ReturnTargetValue>",
            ...
        },
        "CreationDate" : "<ISO 8601 Date String>",
        "StartDate" : "<ISO 8601 Date String>",
        "DueDate" : "<ISO 8601 Date String>",
        "CompletedDate" : "<ISO 8601 Date String>",
    }

.. container::

    Related: :ref:`job-status-label`,
    :ref:`fidelity-label`,
    :ref:`priority-label`
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