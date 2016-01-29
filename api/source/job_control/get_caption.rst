Get Caption
===========

Get the caption file for a job.
The job must have completed transcription before a caption can be downloaded.

**HTTP Method**

.. http:get:: /api/job/get_caption

**Query String Parameters** — Required

+------------------------+----------------------------------------------------------------------------------------+
| Name                   | Details                                                                                |
+========================+==================+=====================================================================+
| v                      | `Description`    | The version of the API to use                                       |
|                        +------------------+---------------------------------------------------------------------+
|                        | `Allowed Values` | 1                                                                   |
|                        +------------------+---------------------------------------------------------------------+
|                        | `Example`        | ``v=1``                                                             |
+------------------------+------------------+---------------------------------------------------------------------+
| api_token              | `Description`    | The API token used for this session                                 |
|                        +------------------+---------------------------------------------------------------------+
|                        | `Allowed Values` | Hex String                                                          |
|                        +------------------+---------------------------------------------------------------------+
|                        | `Example`        | ``api_token=7ca5dc5c7cce449fb0fff719307e8f5f``                      |
+------------------------+------------------+---------------------------------------------------------------------+
| job_id                 | `Description`    | The ID of the job                                                   |
|                        +------------------+---------------------------------------------------------------------+
|                        | `Allowed Values` | Hex String                                                          |
|                        +------------------+---------------------------------------------------------------------+
|                        | `Example`        | ``job_id=64bea283eff6475ea6596027a6ba0929``                         |
+------------------------+------------------+---------------------------------------------------------------------+
| caption_format         | `Description`    | The format of the caption file to return                            |
|                        +------------------+---------------------------------------------------------------------+
|                        | `Allowed Values` | :ref:`caption-format-label`                                         |
|                        +------------------+---------------------------------------------------------------------+
|                        | `Example`        | ``caption_format=SRT``                                              |
+------------------------+------------------+---------------------------------------------------------------------+

**Query String Parameters** — Optional

+---------------------------------+------------------------------------------------------------------------------+
| Name                            | Details                                                                      |
+=================================+==================+===========================================================+
| build_url                       | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Rather than returning the file, return a permanent URL to the</br>          |
|                                 |  file.                                                                       |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | false                                                     |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``build_url=true``                                        |
+---------------------------------+------------------+-----------------------------------------------------------+
| caption_words_min               | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Minimum number of words allowed in a caption.                               |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Integer                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | 1                                                         |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``caption_words_min=3``                                   |
+---------------------------------+------------------+-----------------------------------------------------------+
| caption_by_sentence             | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  When true, puts each sentence into its own caption. When</br>               |
|                                 |  false, more than one sentence may appear in a single</br>                   |
|                                 |  caption.                                                                    |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | true                                                      |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``caption_by_sentence=false``                             |
+---------------------------------+------------------+-----------------------------------------------------------+
| characters_per_caption_line     | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Maximum number of characters to be displayed on each</br>                   |
|                                 |  caption line.                                                               |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Integer                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | 42                                                        |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``characters_per_caption_line=30``                        |
+---------------------------------+------------------+-----------------------------------------------------------+
| dfxp_header                     | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Allows you to specify a custom header for your DFXP</br>                    |
|                                 |  caption file. The header should be the entire contents of</br>              |
|                                 |  the header including the opening and closing <head> tags.<br>               |
|                                 |  Ignored if caption_format does not equal DFXP.                              |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | XML String                                                |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | ""                                                        |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``dfxp_header=<head></head>``                             |
+---------------------------------+------------------+-----------------------------------------------------------+
| disallow_dangling               | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Will prevent captions from having the last word in a sentence</br>          |
|                                 |  start a new line. Last words will ALWAYS be kept on the same</br>           |
|                                 |  line, even if it breaks the characters_per_caption_line option.             |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | false                                                     |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``disallow_dangling=true``                                |
+---------------------------------+------------------+-----------------------------------------------------------+
| display_effects_speaker_as      | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Determines what speaker name should used for sound effects.                 |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | String                                                    |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | Effects                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``display_effects_speaker_as=Sound``                      |
+---------------------------------+------------------+-----------------------------------------------------------+
| display_speaker_id              | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Determines the way speakers are identified in the captions.</br>            |
|                                 |  Choose "no" to not display speaker identities at all:</br>                  |
|                                 |    ">> example"</br>                                                         |
|                                 |  Choose "number" to display only the speaker number:</br>                    |
|                                 |    ">> Speaker 1: example"</br>                                              |
|                                 |  Choose "name" to display the speaker name:</br>                             |
|                                 |    ">> John Doe: example".</br>                                              |
|                                 |  If you choose "name", the speaker number will be displayed</br>             |
|                                 |  if the name is not available.                                               |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | :ref:`speaker-id-label`                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | name                                                      |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``display_speaker_id=number``                             |
+---------------------------------+------------------+-----------------------------------------------------------+
| elementlist_version             | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  The version of element list to generate the captions from.</br>             |
|                                 |  If not specified, the caption will be generated from the</br>               |
|                                 |  latest version.                                                             |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | ISO 8601 Date String                                      |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | ""                                                        |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``elementlist_version=2014-07-31T12:35:52.324389``        |
+---------------------------------+------------------+-----------------------------------------------------------+
| emit_speaker_change_tokens_as   | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Determine what characters to use to denote speaker changes.                 |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | String                                                    |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | ">>"                                                      |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``emit_speaker_change_tokens_as=--``                      |
+---------------------------------+------------------+-----------------------------------------------------------+
| force_case                      | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Force the contents of the captions to be all UPPER or</br>                  |
|                                 |  lower case. If blank, the case of the captions is not</br>                  |
|                                 |  changed.                                                                    |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | :ref:`case-label`                                         |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | ""                                                        |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``force_case=lower``                                      |
+---------------------------------+------------------+-----------------------------------------------------------+
| include_dfxp_metadata           | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  When true, and the caption format requested is DFXP,</br>                   |
|                                 |  the jobs name, ID and language will be added to the DFXP</br>               |
|                                 |  metadata header. When false, these data are omitted from</br>               |
|                                 |  the header.</br>                                                            |
|                                 |  Ignored if caption_format does not equal DFXP.                              |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | true                                                      |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``include_dfxp_metadata=false``                           |
+---------------------------------+------------------+-----------------------------------------------------------+
| layout_target_caption_length_ms | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Captions generated will, on average, be this duration. However,</br>        |
|                                 |  they may vary significantly based on other parameters you set.              |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Integer                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | 5000                                                      |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``layout_target_caption_length_ms=4000``                  |
+---------------------------------+------------------+-----------------------------------------------------------+
| line_break_on_sentence          | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Inserts a line break in between sentences that are in</br>                  |
|                                 |  the same caption.                                                           |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | false                                                     |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``line_break_on_sentence=true``                           |
+---------------------------------+------------------+-----------------------------------------------------------+
| line_ending_format              | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Determine the end of line (EOL) character to use for the</br>               |
|                                 |  captions.                                                                   |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | :ref:`line-ending-label`                                  |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | "UNIX"                                                    |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``line_ending_format=OSX``                                |
+---------------------------------+------------------+-----------------------------------------------------------+
| lines_per_caption               | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Number of lines to be displayed for each caption.                           |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Integer                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | 2                                                         |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``lines_per_caption=3``                                   |
+---------------------------------+------------------+-----------------------------------------------------------+
| mask_profanity                  | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Replace profanity with asterisks.                                           |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | false                                                     |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``mask_profanity=true``                                   |
+---------------------------------+------------------+-----------------------------------------------------------+
| maximum_caption_duration        | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  No captions longer than this (in milliseconds) will be</br>                 |
|                                 |  produced. If not specified, there is no maximum.                            |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Integer                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | None (no maximum)                                         |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``maximum_caption_duration=10000``                        |
+---------------------------------+------------------+-----------------------------------------------------------+
| merge_gap_interval              | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Captions with a gap between them that is smaller than</br>                  |
|                                 |  this (in milliseconds) will have their start and/or</br>                    |
|                                 |  end times changed so there is no time gap between the captions.             |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Integer                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | 1000                                                      |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``merge_gap_interval=1500``                               |
+---------------------------------+------------------+-----------------------------------------------------------+
| minimum_caption_length_ms       | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Extends the duration of short captions to the this minimum</br>             |
|                                 |  length. Additional time is taken from later caption blocks</br>             |
|                                 |  to meet this minimum time.                                                  |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Integer                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | None (no minimum)                                         |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``minimum_caption_length_ms=1500``                        |
+---------------------------------+------------------+-----------------------------------------------------------+
| minimum_gap_between_captions_ms | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Adds a minimum time between captions such as there will</br>                |
|                                 |  always be some time between captions where no text is</br>                  |
|                                 |  displayed. When captions are very close together, time</br>                 |
|                                 |  will be removed from the caption duration to make the gap.                  |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Integer                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | None (no minimum)                                         |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``minimum_gap_between_captions_ms=100``                   |
+---------------------------------+------------------+-----------------------------------------------------------+
| qt_seamless                     | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Does not put time gaps of any kind between caption blocks.</br>             |
|                                 |  Ignored if caption_format does not equal QT.                                |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | false                                                     |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``qt_seamless=true``                                      |
+---------------------------------+------------------+-----------------------------------------------------------+
| remove_disfluencies             | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Remove verbal disfluencies from the generated transcript.</br>              |
|                                 |  Common disfluencies such as "um" and "ah" are removed while</br>            |
|                                 |  maintaining appropriate punctuation.                                        |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | true                                                      |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``remove_disfluencies=false``                             |
+---------------------------------+------------------+-----------------------------------------------------------+
| remove_sounds_list              | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  A list of sounds to not show in the caption. This is a</br>                 |
|                                 |  JSON style list, and should look like ["MUSIC", "LAUGH"].</br>              |
|                                 |  Ignored if remove_sound_references is true.                                 |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` |  :ref:`sound-tag-label`                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | []                                                        |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``remove_sounds_list=["MUSIC","LAUGH"]``                  |
+---------------------------------+------------------+-----------------------------------------------------------+
| remove_sound_references         | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Remove ALL non-verbal sound and noise references from the</br>              |
|                                 |  generated transcript. Sounds and unidentified noises are</br>               |
|                                 |  depicted in the caption as [SOUND], [COUGH] and [NOISE].</br>               |
|                                 |  If this parameter is set, these identifiers are omitted</br>                |
|                                 |  from the caption.                                                           |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | true                                                      |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``remove_sound_references=false``                         |
+---------------------------------+------------------+-----------------------------------------------------------+
| replace_slang                   | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Replace common slang terms from the generated transcript.</br>              |
|                                 |  Common replacements are "want to" for "wanna", "going to"</br>              |
|                                 |  for "gonna", etc.                                                           |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | false                                                     |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``replace_slang=true``                                    |
+---------------------------------+------------------+-----------------------------------------------------------+
| silence_max_ms                  | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  If there is a interval of silence in the middle of a sentence</br>          |
|                                 |  longer than this, then the caption will be split.                           |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Integer                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | 2000                                                      |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``silence_max_ms=1000``                                   |
+---------------------------------+------------------+-----------------------------------------------------------+
| single_speaker_per_caption      | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  When true, puts each speaker into its own caption. When false,</br>         |
|                                 |  more than one speaker may appear in a single caption.                       |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | false                                                     |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``single_speaker_per_caption=true``                       |
+---------------------------------+------------------+-----------------------------------------------------------+
| sound_boundaries                | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Specifies the characters to surround sound references with.</br>            |
|                                 |  The default will generate sound references that look like</br>              |
|                                 |  this: [MUSIC].                                                              |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Character Tuple                                           |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | ('[',']')                                                 |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``sound_boundaries=('{','}')``                            |
+---------------------------------+------------------+-----------------------------------------------------------+
| sound_threshold                 | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Sound references that are longer than this threshold will</br>              |
|                                 |  be made their own caption entirely, and will not have any</br>              |
|                                 |  text included with them. If not set, Sound references will</br>             |
|                                 |  be included back to back with text no matter the duration of</br>           |
|                                 |  the sound.                                                                  |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Integer                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | None                                                      |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``sound_threshold=5000``                                  |
+---------------------------------+------------------+-----------------------------------------------------------+
| sound_tokens_by_caption         | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  If true, all sound references will always be in their own</br>              |
|                                 |  caption. If false, more than one sound reference may</br>                   |
|                                 |  appear in a single caption.                                                 |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | false                                                     |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``sound_tokens_by_caption=true``                          |
+---------------------------------+------------------+-----------------------------------------------------------+
| sound_tokens_by_line            | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  If true, all sound references will always be in their own</br>              |
|                                 |  line. If false, more than one sound reference may appear</br>               |
|                                 |  in a single line.                                                           |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | false                                                     |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``sound_tokens_by_line=true``                             |
+---------------------------------+------------------+-----------------------------------------------------------+
| sound_tokens_by_caption_list    | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  If non-empty, the specified sound references will always</br>               |
|                                 |  be in their own caption. If empty, more than one</br>                       |
|                                 |  sound reference may appear in a single caption.</br>                        |
|                                 |  Ignored if sound_tokens_by_caption is true.                                 |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` |  :ref:`sound-tag-label`                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | ["BLANK_AUDIO","MUSIC"]                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``sound_tokens_by_caption_list=[]``                       |
+---------------------------------+------------------+-----------------------------------------------------------+
| sound_tokens_by_line_list       | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  If non-empty, the specified sound references will always</br>               |
|                                 |  be in their own line. If empty, more than one</br>                          |
|                                 |  sound reference may appear in a single line.</br>                           |
|                                 |  Ignored if sound_tokens_by_line is true.                                    |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` |  :ref:`sound-tag-label`                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | ["BLANK_AUDIO","MUSIC]                                    |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``sound_tokens_by_line_list=["NOISE"]``                   |
+---------------------------------+------------------+-----------------------------------------------------------+
| speaker_on_new_line             | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  If true, a speaker change will cause a new caption to be</br>               |
|                                 |  made. If false, multiple speakers may appear in a single</br>               |
|                                 |  caption.                                                                    |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | true                                                      |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``speaker_on_new_line=false``                             |
+---------------------------------+------------------+-----------------------------------------------------------+
| srt_format                      | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  If the caption format is SRT, determines what the caption</br>              |
|                                 |  blocks will look like. The default, prints caption blocks</br>              |
|                                 |  that look like this:</br></br>                                              |
|                                 |  &nbsp;&nbsp;&nbsp;1:</br>                                                   |
|                                 |  &nbsp;&nbsp;&nbsp;00:00:06,060 --> 00:00:16,060</br>                        |
|                                 |  &nbsp;&nbsp;&nbsp;This is the caption text.</br></br>                       |
|                                 |  You can alter the caption block by re-arranging or removing</br>            |
|                                 |  the substitution string values, shown enclosed in braces "{}"</br>          |
|                                 |  in the default value below. Substitution strings may used</br>              |
|                                 |  more than once if desired. Any text that is not a substitution</br>         |
|                                 |  string will be displayed as written. To add new lines, include</br>         |
|                                 |  a \n. Note, you may need to escape the \n with an extra</br>                |
|                                 |  backslash when encoding the request.                                        |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | String                                                    |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | .. raw:: html                                             |
|                                 |                  |                                                           |
|                                 |                  |  {caption_number:d}\n{start_hour:02d}:</br>               |
|                                 |                  |  {start_minute:02d}:{start_second:02d},</br>              |
|                                 |                  |  {start_millisecond:03d} -->{end_hour:02d}:</br>          |
|                                 |                  |  {end_minute:02d}:{end_second:02d},</br>                  |
|                                 |                  |  {end_millisecond:03d}\n{caption_text}\n\n                |
|                                 |                  |                                                           |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``srt_format=...``                                        |
+---------------------------------+------------------+-----------------------------------------------------------+
| strip_square_brackets           | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Removes all square brackets like '[' or ']' from captions.</br>             |
|                                 |  By default square brackets surround sound references like</br>              |
|                                 |  '[MUSIC]', but they may exist as part of the caption text as well.          |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | false                                                     |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``strip_square_brackets=true``                            |
+---------------------------------+------------------+-----------------------------------------------------------+
| utf8_mark                       | .. raw:: html                                                                |
|                                 |                                                                              |
|                                 |  Adds a utf8 bytemark to the beginning of the caption. This</br>             |
|                                 |  should only be used if the system you are loading the caption</br>          |
|                                 |  files into needs a byte marker. The vast majority of systems</br>           |
|                                 |  do not.                                                                     |
|                                 |                                                                              |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Allowed Values` | Boolean                                                   |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Default Value`  | false                                                     |
|                                 +------------------+-----------------------------------------------------------+
|                                 | `Example`        | ``utf8_mark=true``                                        |
+---------------------------------+------------------+-----------------------------------------------------------+

**Responses**

    Returns requested caption file as body data, or if **build_url** was set to true returns caption URL.

+-----------+------------------------------------------------------------------------------------------+
| HTTP Code | Details                                                                                  |
+===========+===============+==========================================================================+
| 200       | `Description` | Success                                                                  |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | .. code-block:: javascript                                               |
|           |               |                                                                          |
|           |               |  Caption file as body data                                               |
+-----------+---------------+--------------------------------------------------------------------------+
| 200       | `Description` | Success                                                                  |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | .. code-block:: javascript                                               |
|           |               |                                                                          |
|           |               |  {                                                                       |
|           |               |    "CaptionUrl": "Hosted URL"                                            |
|           |               |  }                                                                       |
+-----------+---------------+--------------------------------------------------------------------------+
| 400       | `Description` | An error occurred                                                        |
|           +---------------+--------------------------------------------------------------------------+
|           | `Contents`    | .. code-block:: javascript                                               |
|           |               |                                                                          |
|           |               |  {                                                                       |
|           |               |    "ErrorType": "ERROR_TYPE_ENUM",                                       |
|           |               |    "ErrorComment": "Description of error details."                       |
|           |               |  }                                                                       |
|           |               |                                                                          |
|           |               | .. container::                                                           |
|           |               |                                                                          |
|           |               |    See :ref:`error-format-label` for details.                            |
|           |               |                                                                          |
+-----------+---------------+--------------------------------------------------------------------------+

**Example Requests**

.. sourcecode:: http

    GET /api/job/get_caption?v=1&api_token=7ca5dc5c7cce449fb0fff719307e8f5f
    &job_id=64bea283eff6475ea6596027a6ba0929&caption_format=SRT HTTP/1.1
    Host: api.cielo24.com

**Example Response**

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: text/plain

    1
    00:02:17,440 --> 00:02:20,375
    Some text on first line.

    2
    00:02:20,476 --> 00:02:22,501
    More text on second line.

.. sourcecode:: http

    HTTP/1.1 200 OK
    Content-Type: application/json

    { "CaptionUrl": "http://domain.com/path/file.srt" }