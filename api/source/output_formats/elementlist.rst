.. _elementlist-label:

ElementList Format
==================

An ElementList is JSON encoded data that contains words, timing, and some metadata of a transcript.
The JSON data structures that comprise an ElementList are defined below.
All API calls expect and return ElementList version 3 data structures.
An example ElementList can be found :doc:`here <example_elementlist>`.

JSON Definitions
----------------

**ElementList:**

.. code-block:: javascript

    {
        /* The ElementList format version. Currently 2. */
        "version" : "<Integer>",

        /* The start time of the ElementList relative to the media associated with it.
         * Typically this is 0. */
        "start_time" : "<Integer (milliseconds)>",

        /* The end time of the ElementList relative to the media associated with it.
         * Typically this is the length of the media. */
        "end_time" : "<Integer (milliseconds)>",

        /* The language of the ElementList. */
        "language" : "<String (RFC 5646 Language Code)>",

        /* A list of segments (see definition below).
         * This variable is required, but can contain an empty list. */
        "segments" : [<Segment>],

        /* A list of speakers (see definition below).
         * This variable is optional. */
        "speakers" : [<Speaker>]
    }


.. _speaker-format-label:

**Speaker:**

.. code-block:: javascript

    {
        /* The speaker’s name.
         * This variable is required, but it can be empty. */
        "name" : "<String>",

        /* The speaker’s identifier. Sequential number starting from 1.
         * This variable is required and it cannot be empty. */
        "id" : "<Integer>",

        /* The speaker’s gender (MALE, FEMALE or UNKNOWN).
         * This variable is required, but it can be empty. */
        "gender" : "<SpeakerGender Enum>"
    }

.. container::

    Related: :ref:`speaker-gender-label`.

.. raw:: html

    </br>

.. _segment-format-label:

**Segment:**

.. code-block:: javascript

    {
        /* If true, this segment is spoken by a different speaker than the previous segment. */
        "speaker_change" : "<Boolean>",

        /* The identifier of this segment’s speaker. The speaker must be
         * in the ElementList’s speakers list. This variable is optional. */
        "speaker_id" : "<Boolean>",

        /* Reserved for future use. This variable is optional. */
        "interpolated" : "<Boolean>",

        /* The start time of the segment relative to the media associated with it. */
        "start_time" : "<Integer (milliseconds)>",

        /* The end time of the segment relative to the media associated with it. */
        "end_time" : "<Integer (milliseconds)>",

        /* A list of sequences (see definition below).
         * This variable is required, but can contain an empty list. */
        "sequences" : [<Sequence>]
    }

.. _sequence-format-label:

**Sequence:**

.. code-block:: javascript

    {
        /* Reserved for future use. This variable is optional. */
        "interpolated" : "<Boolean>",

        /* The start time of the sequence relative to the media associated with it. */
        "start_time" : "<Integer (milliseconds)>",

        /* The end time of the sequence relative to the media associated with it. */
        "end_time" : "<Integer (milliseconds)>",

        /* Reserved for future use. This variable is optional. */
        "confidence_score" : "<Float>",

        /* A list of tokens (see definition below).
         * This variable is required, but can contain an empty list. */
        "tokens" : [<Token>]
    }

.. _token-format-label:

**Token:**

.. code-block:: javascript

    {
        /* If true, the timing for this token has been interpolated.
         * If false, the timing for this token has been generated
         * by an ASR or human. */
        "interpolated" : "<Boolean>",

        /* The start time of the token relative to the media that it is associated with. */
        "start_time" : "<Integer (milliseconds)>",

        /* The end time of the token relative to the media that it is associated with. */
        "end_time" : "<Integer (milliseconds)>",

        /* The string value of the token. Should always be lowercase. */
        "value" : "<String>",

        /* The type of token. */.
        "type" : "<TokenType Enum>",

        /* The display value of the token.
         * May be mixed case or otherwise different than the word value. */
        "display_as" : "<String>",

        /* A list of tags. */
        "tags" : [<Tag Enum>]
    }

.. container::

    Related: :ref:`token-type-label`, :ref:`sound-tag-label`.

.. raw:: html

    </br>

Additional Notes
----------------

    #. All times are in whole milliseconds (no decimal places) referenced from the start of the media.
    #. The times of segment, sequences, and tokens are not permitted to overlap.
    #. All times must be positive.
    #. Zero duration segment, sequences, and tokens are not permitted.
    #. The *ENDS_SENTENCE* tag should be placed in the token for punctuation that ends the sentence. Typically this is a period, question mark, or exclamation point. However, it can be any valid token.
    #. There should be only one sentence per segment.
    #. There should be only one speaker per segment.
    #. Sequences should contain tokens that should not be separated by whitespace, such as a word and the punctuation associated with it.