Enumeration Types
=================

Enumeration types used in cielo24 API.

.. _task-type-label:

Task Type Enumeration
---------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    JOB_CREATED</br>
    <span style="padding: 20px">
    JOB_DELETED</br>
    <span style="padding: 20px">
    JOB_ADD_MEDIA</br>
    <span style="padding: 20px">
    JOB_ADD_TRANSCRIPT</br>
    <span style="padding: 20px">
    JOB_PERFORM_TRANSCRIPTION</br>
    <span style="padding: 20px">
    JOB_PERFORM_PREMIUM_SYNC</br>
    <span style="padding: 20px">
    JOB_UPDATE_ELEMENTLIST</br>
    <span style="padding: 20px">
    JOB_GET_TRANSCRIPT</br>
    <span style="padding: 20px">
    JOB_GET_CAPTION</br>
    <span style="padding: 20px">
    JOB_GET_ELEMENTLIST</br>
    </font>

.. _error-type-label:

Error Type Enumeration
----------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    LOGIN_INVALID <font color="black">- Incorrect username or password was supplied as login credentials. Check that the the correct username and password are being sent.</font></br>
    <span style="padding: 20px">
    ACCOUNT_EXISTS <font color="black">- Attempted to create an account that already exists. Login with the account, or create one with a different name.</font></br>
    <span style="padding: 20px">
    ACCOUNT_UNPRIVILEGED <font color="black">- You are attempting to modify information of an account you do not have access to. You must be the owner, parent, or an administrator to modify an account’s information.</font></br>
    <span style="padding: 20px">
    BAD_API_TOKEN <font color="black">- You have provided an incorrect API token. Either the session has gone valid, or the token provided was incorrect. Re-login to get a new session, or check that you submitted the correct token.</font></br>
    <span style="padding: 20px">
    INVALID_QUERY <font color="black">- You passed a parameter or other information that could not be used for this command, see the ErrorComment for more specific information.</font></br>
    <span style="padding: 20px">
    INVALID_OPTION <font color="black">- You supplied an option for a parameter that wasn't in it's approved option list. Please check the option list and try again.</font></br>
    <span style="padding: 20px">
    MISSING_PARAMETER <font color="black">- You did not supply a required parameter for this function, see the ErrorComment for which parameter was missing.</font></br>
    <span style="padding: 20px">
    INVALID_URL <font color="black">- You have provided a URL for a callback, media URL, or other URL that could not be accessed. Check the URL is correct, and try again.</font></br>
    <span style="padding: 20px">
    ITEM_NOT_FOUND <font color="black">- You have provided an ID for a Job, task, billing item, contact info, or other item, that could not be found in the system. See the ErrorComment for more details on the item that was not found.</font></br>
    </font>

.. _job-status-label:

Job Status Enumeration
----------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    Authorizing</br>
    <span style="padding: 20px">
    Pending</br>
    <span style="padding: 20px">
    In Process</br>
    <span style="padding: 20px">
    Complete</br>
    <span style="padding: 20px">
    Media Failure</br>
    <span style="padding: 20px">
    Reviewing</br>
    </font>

.. _task-status-label:

Task Status Enumeration
-----------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    COMPLETE</br>
    <span style="padding: 20px">
    INPROGRESS</br>
    <span style="padding: 20px">
    ABORTED</br>
    <span style="padding: 20px">
    FAILED</br>
    </font>

.. _priority-label:

Priority Enumeration
--------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    STANDARD</br>
    <span style="padding: 20px">
    PRIORITY</br>
    </font>

.. _fidelity-label:

Fidelity Enumeration
--------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    MECHANICAL</br>
    <span style="padding: 20px">
    PREMIUM</br>
    <span style="padding: 20px">
    PROFESSIONAL</br>
    </font>

.. _job-difficulty-label:

JobDifficulty Enumeration
-------------------------

.. raw:: html

    Indicates whether the job was difficult to process. This difficulty could be due to issues with media quality, cross-talk and background noise in the audio, strong accents of speakers, or complicated subject matter. The value of this field will update as the job is processed but will not change once the job has completed.
    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    Good
    <font color="black"> - The job was processed without any major problems.</font>
    </br>
    <span style="padding: 20px">
    Bad
    <font color="black"> - A significant amount of the job was difficult to process. This may cause a delay of the expected due date.</font>
    </br>
    <span style="padding: 20px">
    Unknown
    <font color="black"> - Not enough of the job has been analyzed at this time to determine whether it is difficult.</font>
    </br>
    </font>

.. _caption-format-label:

Caption Format Enumeration
--------------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    SRT</br>
    <span style="padding: 20px">
    SBV</br>
    <span style="padding: 20px">
    DFXP</br>
    <span style="padding: 20px">
    QT</br>
    <span style="padding: 20px">
    TRANSCRIPT</br>
    <span style="padding: 20px">
    TWX</br>
    <span style="padding: 20px">
    TPM</br>
    <span style="padding: 20px">
    WEB_VTT</br>
    <span style="padding: 20px">
    ECHO</br>
    </font>

.. _token-type-label:

Token Type Enumeration
----------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    word
    <font color="black"> - Used to denote a word in the transcript.</font>
    </br>
    <span style="padding: 20px">
    punctuation
    <font color="black"> - Used to denote punctuation in the transcript.</font>
    </br>
    <span style="padding: 20px">
    sound
    <font color="black"> - Used to denote a sound or other non-word item in a transcript. If specified, a tag must also be specified on the token.</font>
    </br>
    </font>

.. _sound-tag-label:

Sound Tag Enumeration
---------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    UNKNOWN</br>
    <span style="padding: 20px">
    INAUDIBLE</br>
    <span style="padding: 20px">
    CROSSTALK</br>
    <span style="padding: 20px">
    MUSIC</br>
    <span style="padding: 20px">
    NOISE</br>
    <span style="padding: 20px">
    LAUGH</br>
    <span style="padding: 20px">
    COUGH</br>
    <span style="padding: 20px">
    FOREIGN</br>
    <span style="padding: 20px">
    BLANK_AUDIO</br>
    <span style="padding: 20px">
    APPLAUSE</br>
    <span style="padding: 20px">
    BLEEP</br>
    <span style="padding: 20px">
    ENDS_SENTENCE
    <font color="black"> - Used to denote that this token ends the current sentence.</font>
    </br>
    </font>

.. _speaker-id-label:

Speaker ID Enumeration
----------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    no</br>
    <span style="padding: 20px">
    number</br>
    <span style="padding: 20px">
    name</br>
    </font>

.. _speaker-gender-label:

Speaker Gender Enumeration
--------------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    UNKNOWN</br>
    <span style="padding: 20px">
    MALE</br>
    <span style="padding: 20px">
    FEMALE</br>
    </font>

.. _line-ending-label:

Line Ending Enumeration
-----------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    UNIX</br>
    <span style="padding: 20px">
    WINDOWS</br>
    <span style="padding: 20px">
    OSX</br>
    </font>

.. _case-label:

Case Enumeration
----------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    upper</br>
    <span style="padding: 20px">
    lower</br>
    <span style="padding: 20px">
    ""<font color="black">- (Empty string) represents unchanged case.</font></br>
    </font>

Customer Approval Steps Enumeration
-----------------------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    TRANSLATION</br>
    <span style="padding: 20px">
    RETURN</br>
    </font>

Customer Approval Tools Enumeration
-----------------------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    AMARA</br>
    <span style="padding: 20px">
    CIELO24</br>
    </font>

.. _iwp-label:

IWP Enumeration
---------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    PREMIUM</br>
    <span style="padding: 20px">
    INTERIM_PROFESSIONAL</br>
    <span style="padding: 20px">
    PROFESSIONAL</br>
    <span style="padding: 20px">
    SPEAKER_ID</br>
    <span style="padding: 20px">
    FINAL</br>
    <span style="padding: 20px">
    MECHANICAL</br>
    <span style="padding: 20px">
    CUSTOMER_APPROVED_RETURN</br>
    <span style="padding: 20px">
    CUSTOMER_APPROVED_TRANSLATION</br>
    </font>
