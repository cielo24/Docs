Enumeration Types
=================

Enumeration types used in cielo24 API.

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
    </font>

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

Priority Enumeration
--------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    ECONOMY</br>
    <span style="padding: 20px">
    STANDARD</br>
    <span style="padding: 20px">
    PRIORITY</br>
    <span style="padding: 20px">
    CRITICAL</br>
    <span style="padding: 20px">
    HIGH</br>
    </font>

Fidelity Enumeration
--------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    MECHANICAL</br>
    <span style="padding: 20px">
    HIGH</br>
    <span style="padding: 20px">
    EXTERNAL</br>
    <span style="padding: 20px">
    PREMIUM</br>
    <span style="padding: 20px">
    PROFESSIONAL</br>
    </font>

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

Token Type Enumeration
----------------------

.. raw:: html

    <font color="firebrick">
    <p>
    <span style="padding: 20px">
    word</br>
    <span style="padding: 20px">
    punctuation</br>
    <span style="padding: 20px">
    sound</br>
    </font>

Sound Tag Enumeration
---------------

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
    </font>

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

IWP Enumeration
-----------------------------------

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