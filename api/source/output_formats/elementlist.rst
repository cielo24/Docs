.. _elementlist-label:

ElementList Format
==================

An ElementList is JSON encoded data that contains words, timing, and some metadata of a transcript.
The JSON data structures that comprise an ElementList are defined below.
All API calls expect and return ElementList version 2 data structures.
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
        "speakers" : [<Speaker>],

        /* A dictionary of keywords (see definition below).
         * This variable is optional. */
        "keywords" : { "<keyword_value>" : "<Keyword>", },

        /* A dictionary of topics (see definition below).
         * This variable is optional. */
        "topics" : { "<topic_name>" : "<Topic>", },

        /* A dictionary of entities (see definition below).
         * This variable is optional. */
        "entities" : { "<entity_name>" : "<Entity>", }
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
        "speaker_id" : "<Integer>",

        /* Reserved for future use. This variable is optional. */
        "interpolated" : "<Boolean>",

        /* The start time of the segment relative to the media associated with it. */
        "start_time" : "<Integer (milliseconds)>",

        /* The end time of the segment relative to the media associated with it. */
        "end_time" : "<Integer (milliseconds)>",

        /* A list of sequences (see definition below).
         * This variable is required, but can contain an empty list. */
        "sequences" : [<Sequence>],

	/*  Reserved for future use. This variable is optional. */
 	"style": "<String>"
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
        "tokens" : [<Token>],

	/*  Reserved for future use. This variable is optional. */
        "style": "<String>"
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
        "tags" : [<Tag Enum>],

	/*  Reserved for future use. This variable is optional. */
        "style": "<String>"
    }

.. container::

    Related: :ref:`token-type-label`, :ref:`sound-tag-label`.

.. raw:: html

    </br>

.. _media-intelligence-label:

**Entity, Topic and Keyword:**

    The entity/keyword/topic portions of the ElementList contain metadata related
    to the contents of the ElementList.

.. note::
    The time ranges for the meta data may not exactly match token or segment 
    boundaries.

.. note::
    The text of some entities/keywords/topics may have been inferred by the content
    of the transcript and may not actually appear in the ElementList.

.. note::
    The actual entity/keyword/topic is the "key" in the dictionary. It is always lowercase 
    and will not be duplicated. The following data construct is the "value" associated with
    the "key".

.. note::
    The display_name may differ from the "key", typically in capitalization, but sometimes
    there are other differences.

.. code-block:: javascript

    "keyword (key)": {
        /* The display value of the entity/keyword/topic.
         * May be mixed case or otherwise different than the key value. */
        "display_name": "<String>",

        /* A URL to an external resource related to this entity/keyword/topic. */
        "url": "<String (URL)>",

        /* A list of time ranges to which the entity/keyword/topic is related. */
        "time_ranges": [
            {
                "start_time": "<Integer (milliseconds)>",
                "end_time:": "<Integer (milliseconds)>"
            },
        ]
    }

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
