JSON Formats
============

Below are the descriptions of the formats used in cielo24 API.

Job Info Format
---------------

The following defines the Job Info in JSON format:

.. code-block:: javascript

    {
        "JobId" : "<Guid HexString>",
        "JobName" : "<String>",
        "Language" : "<RFC 5646 Language Code>",
        "Tasks" :
        [
            "List of Task Statuses (see below)"
        ]
    }

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

.. raw:: html

    Related: <a href="enums.html#task-status-enumeration">Task Status</a>,
    <a href="enums.html#task-type-enumeration">Task Type</a>.</br></br>

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

Job Format
----------

The following defines the Job in JSON format:

.. code-block:: javascript

    {
        "JobId" : "<Guid HexString>",
        "JobName" : "<String>",
        "JobStatus" : "<JobStatus Enum>",
        "Priority" : "<Priority Enum>",
        "Fidelity" : "<Fidelity Enum>",
        "JobLanguage" : "<RFC 5646 Language Code>",
        "TargetLanguage" : "<RFC 5646 Language Code>",
        "CreationTime" : "<ISO 8601 Date String>",
        "DueDate" : "<ISO 8601 Date String>",
        "TurnaroundTimeHours" : "<Integer>",
        "StartTime" : "<ISO 8601 Date String>",
        "CompletedTime" : "<ISO 8601 Date String>"
    }

.. raw:: html

    Related: <a href="enums.html#job-status-enumeration">Job Status</a>,
    <a href="enums.html#fidelity-enumeration">Fidelity</a>,
    <a href="enums.html#priority-enumeration">Priority</a>.</br></br>

Error Format
------------

The following defines the Error Output in JSON format:

.. code-block:: javascript

    {
        "ErrorType" : "<ErrorType Enum>",
        "ErrorComment" : "<String>"
    }

.. raw:: html

    Related: <a href="enums.html#error-type-enumeration">Error Type</a>.</br></br>

ElementList Format
------------------

The ElementList format is defined in the cielo24 ElementList format specification.
All API calls expect and return ElementList version 3 data structures.

.. code-block:: javascript

    {
        "version" : "<Integer>",
        "start_time" : "<Integer (milliseconds)>",
        "end_time" : "<Integer (milliseconds)>",
        "language" : "<RFC 5646 Language Code>",
        "segments" :
        [
            "List of Segments (see below)",
        ],
        "speakers" :
        [
            "List of Speakers (see below)",
        ]
    }

Speaker Format
--------------

The following defines the Speaker in JSON format:

.. code-block:: javascript

    {
        "name" : "<String>",
        "id" : "<Integer>",
        "gender" : "<SpeakerGender Enum>"
    }

.. raw:: html

    Related: <a href="enums.html#speaker-gender-enumeration">Speaker Gender</a>.</br></br>

Segment Format
--------------

The following defines the Segment in JSON format:

.. code-block:: javascript

    {
        "speaker_change" : "<Boolean>",
        "speaker_id" : "<Boolean>",
        "interpolated" : "<Boolean>",
        "start_time" : "<Integer (milliseconds)>",
        "end_time" : "<Integer (milliseconds)>",
        "sequences" :
        [
            "List of Sequences (see below)"
        ]
    }

Sequence Format
---------------

The following defines the Sequence in JSON format:

.. code-block:: javascript

    {
        "interpolated" : "<Boolean>",
        "start_time" : "<Integer (milliseconds)>",
        "end_time" : "<Integer (milliseconds)>",
        "confidence_score" : "<Float>",
        "tokens" :
        [
            "List of Tokens (see below)"
        ]
    }

Token Format
------------

The following defines the Token in JSON format:

.. code-block:: javascript

    {
        "interpolated" : "<Boolean>",
        "start_time" : "<Integer (milliseconds)>",
        "end_time" : "<Integer (milliseconds)>",
        "value" : "<String>",
        "type" : "<TokenType Enum>",
        "display_as" : "<String>",
        "tags" :
        [
            "List of Tag Enums"
        ]
    }

.. raw:: html

    Related: <a href="enums.html#token-type-enumeration">Token Type</a>.</br></br>

ElementList List Format
-----------------------

The following defines the ElementList list in JSON format:

.. code-block:: javascript

    [{
        "iwp_name" : "<String>",
        "version" : "<ISO 8601 Date String>"
    }]