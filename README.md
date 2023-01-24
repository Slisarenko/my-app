# Exemplar Schema - Early, Developing, Consolidating and Extending

The exemplar schema is as follows:

```json
{
    "json_version": "1.0",
    "title": "Title of Exemplar",
    "stage": "",
    "text_type": "",
    "additional_text_types": [],
    "collection": "",
    "order": 1,
    "thumbnail": {
        "url": "earlyimages/exemplar-title-thumb.jpg"
    },
    "teacher_focus": [],
    "section_labels": [],
    "language_feature_labels": [],
    "content": {}
}
```

- _json_version_: The latest early exemplar JSON version is "1.0"
- _title_: The title of the exemplar
- _stage_: The stage of the exemplar. For Early Exemplars this should be "Early" (case sensitive).
- _text_type_: The text type of the exemplar. This should be one of the following (case sensitive):
  - "Recount"
  - "Description"
  - "Information Report"
  - "Narrative"
  - "Procedure"
  - "Exposition"
  - "Explanation"
  - "Discussion"
  - "Response"
  - "Hybrid"
- _# Exemplar Schema - Early, Developing, Consolidating and Extending

The exemplar schema is as follows:

```json
{
    "json_version": "1.0",
    "title": "Title of Exemplar",
    "stage": "",
    "text_type": "",
    "additional_text_types": [],
    "collection": "",
    "order": 1,
    "thumbnail": {
        "url": "earlyimages/exemplar-title-thumb.jpg"
    },
    "teacher_focus": [],
    "section_labels": [],
    "language_feature_labels": [],
    "content": {}
}
```

- _json_version_: The latest early exemplar JSON version is "1.0"
- _title_: The title of the exemplar
- _stage_: The stage of the exemplar. For Early Exemplars this should be "Early" (case sensitive).
- _text_type_: The text type of the exemplar. This should be one of the following (case sensitive):
  - "Recount"
  - "Description"
  - "Information Report"
  - "Narrative"
  - "Procedure"
  - "Exposition"
  - "Explanation"
  - "Discussion"
  - "Response"
  - "Hybrid"
- _additional_text_types_: For Hybrid exemplars, there will be additional text types associated. This should be an array of _text_type_ values.
- _collection_: The name of the collection to which this exemplar belongs. Examples include "Early A", "Early B".
- _order_: The order in which the exemplar appears in the book
- _thumbnail_: a relative path to the thumbnail image for the exemplar 

## Teacher Focus

The teacher_focus is an array that captures all the teacher focus notes at the top of each screen. Each object in the array has:

- _screen_: The name of the screen. This should be one of the following (case sensitive):
  - "Text Presentation"
  - "Text Structure"
  - "Language Features"
- _content_: The content of the teacher focus section saved as markdown. Please use line breaks for content over multiple lines. Please do not include content for "Access your Digital Exemplar here" or "Access more Explicit Teaching Strategies here" from this panel.

```json
{
    "screen": "Text Presentation",
    "content": "__Markdown__ content that _can_ include \nLine breaks."
},
{
    "screen": "Text Structure",
    "content": "__Markdown__ content that _can_ include \nLine breaks."
},
{
    "screen": "Language Features",
    "content": "__Markdown__ content that _can_ include \nLine breaks."
}
```

![Teacher Focus Example](teacher-focus.png)

## Section Labels

The section_labels is an array that captures the content explaining each of the sections on the text structure page. Each object in the array has:

- _label_: The name of the section shown in the darker coloured boxes.
- _description_: The description of the section shown in the lighter coloured boxes. This can be empty if the section doesn't have a description.

```json
{
    "label": "Title",
    "description": ""
},
{
    "label": "General Statement",
    "description": "What are the living or non-living things?"
},
```

![Section Labels Example](section-labels.png)

## Language Feature Labels

The language_feature_labels is an array that captures the content explaining each of the language features on the text structure page. Each object in the array has:

- _label_: The name of the language feature.

```json
{
    "label": "Nouns"
},
{
    "label": "Adjectives"
},
```

![Language Feature Labels Example](language-feature-labels.png)

Allowed language features labels:
- 'Nouns'
- 'Past-tense verbs'
- 'Time and sequence words'
- 'Adjectives'
- 'Present-tense verbs'
- 'Present-tense verbs (_to direct the reader_)'
- 'Present-tense relating verbs'
- 'Present-tense relating verbs (_is_, _are_, _has_, _have_)'
- 'Sensing verbs'
- 'Sensing verbs (_to describe feelings_)'
- 'Conjunctions'
- 'Conjunctions (_if_, _but_, _so_, _because_)'
- 'Conjunctions (_if_, _but_, _so_, _because_, _than_)'
- 'Conjunctions/Text connectives'
- 'Text connectives'
- 'Prepositional phrases'
- 'Phrases'
- 'Adverbs'

*Such language features as: 'Phrases' and 'Prepositional phrases' couldn't exist together, in one exemlar*
## Content

For Early Exemplars, the words and sentences across the different screens are the same, just displayed differently. So the content object must contain enough details to display the exemplar over all 3 screens.

The content is separated into `left` and `right` panels:

```json
{
    "content": {
        "left": [],
        "right": []
    }
}
```

Within each panel is an array that contains sections and/or images.

![Content Example](content-example.png)

Some exemplars may have content, such as an image, that spans both left and right panels at the bottom of the exemplar. In this situation a `bottom` panel can be included:

```json
{
    "content": {
        "left": [],
        "right": [],
        "bottom": []
    }
}
```

### Sections

Each section contains the text from the section block on the text structure page. The schema is as follows:

- _type_: This is always "section"
- _label_: Optional - The name of the section. If used, this **_must_** match a label in the section_labels array for the exemplar. If a section appears on both left and right panels, then the same label may be used. If the section is not labelled in the Text Structure screen, this may be omitted.
- _style_: Any special text styles for the section are mentioned here as an array of strings. This may contain any of the following values:
  - On a title section, include the value `"heading"`
  - On a section where text is right-aligned, include the value `"right-aligned"` 
- _color_: Optional - the colour of the text as displayed on the "Text Presentation" screen
- _lines_: An array of lines of text, which is explained below.

```json
{
    "type": "section",
    "label": "Title",
    "style": ["heading", "right-aligned"],
    "color": "A5D9EB",
    "lines": [
        ...
    ]
},
{
    "type": "section",
    "label": "General Statement",
    "lines": [
        ...
    ]
},
```

![Section Example](section-example.png)

### Sections, Lines and Words

Each section contains an array of lines, and each line contains an array of words:

```json
{
    "type": "section",
    "label": "General Statement",
    "lines": [
        {
            "words": [
                {
                    "text": "Show",
                    "language": "Nouns"
                },
                {
                    "text": "animals",
                    "language": "Nouns"
                },
                {
                    "text": "are",
                    "language": "Present-tense verbs"
                },
                {
                    "text": "animals",
                    "language": "Nouns"
                }
            ]
        },
        {
            "words": [
                {
                    "text": "that"
                },
                {
                    "text": "can",
                    "language": "Present-tense verbs"
                },
                {
                    "text": "win",
                    "language": "Present-tense verbs"
                },
                ...
            ]
        }
    ]
},
```

Each line uses the following schema:

- _words_: an array of word objects for the line
- _style_: this is an array, used for some styles applied to an entire line of words, such as `sub-heading`, `ordered-list` and `unordered-list`. These styles are only required for the [Procedure](procedure.md) text type. If not needed it can be excluded. 
- _sequence_number_: in the case of a line with an `ordered-list` style, this will store the number shown next to the line of words. If not needed it can be excluded.  

```json
{
    "words": [
        {
            "text": "Open"
        }
    ],
    "style": ["ordered-list"],
    "sequence_number": "3."
}
```

Each line must be a separate line object, even if it breaks a sentence into multiple lines.

Some sections may contain an empty line to separate two lines of text. These should be stored as a separate line object with an empty words array.

```json
{
    "words": []
}
```

![Empty Line Example](empty-line-example.png)

Each word uses the following schema:

- _text_: The word to be displayed on the page. **Notes:**
   - Please avoid storing space characters in the text property as it will lead to inconsistent spacing between words on the Language Features screen.
   - Please include apostrophes as part of the word text e.g. `That’s`.
   - Please store other punctuation characters (e.g. `,` `.` `!` `?` `“` `”`) as separate word objects.
- _text_type_: Optional - If the word is highlighted as a text type (e.g. a dotted underline) on the text presentation screen, it should be given this property set to the second value of . If unset, it will be assumed false.
- _language_: If the word is highlighted on the language features screen, it should be given a "language" value which **_must_** match a label in the language_feature_labels array for the exemplar. Otherwise, this should be excluded.
- _prepositional_phrase_: Optional - If the word is highlighted as a prepositional phrase (e.g. a dotted underline) on the language features screen, it should be given this property set to true. If unset, it will be assumed false. For Developing, Consolidating and Extending exemplars only.
- _phrase_: Optional - If the word is highlighted as a phrase (e.g. a solid underline) on the language features screen, it should be given this property set to true. If unset, it will be assumed false. For Extending exemplars only.
- _style_: Optional - This is used to apply bold/italics and other styles to words (see below), otherwise it can be excluded. These values cannot be repeated in the same array, like: *"style": ["bold", "bold"]*

```json
{
    "text": "Cows",
    "language": "Nouns",
    "prepositional_phrase": false,
    "phrase": false,
    "style": [
        "bold",
        "italic"
    ]
}
```

The following _style_ values may be applied to words:
- `"bold"`: Display the word with a bold font weight
- `"italic"`: Display the word with an italicised font style
- `"nospacing"`: A gap is normally added between words when they are displayed. This style removes the gap **_before_** the word object so that it is adjacent to the previous word. This is used:
   - on punctuation such as `,` `.` and `”` (closing quotes) so that there is no space between it and the previous word.

       !["nospacing" on Punctuation](word-nospacing-punctuation.png)
   - on a word **_after_** `“` (opening quotes) so that there is no space between the word an the quote marks.

       !["nospacing" on Following word](word-nospacing-word.png)
- `"separate-next"`: If two or more consecutive words have the same language feature, then they will be highlighted together as a single language feature. This style breaks the highlighting between this word and the **_next_** word so that they are highlighted as separate language features.

    ![Separate Next Style](separate-next.png)
- `"separate-next-phrase"`: Similar to `"separate-next"`, but for phrases. If two or more consecutive words have the same phrase (`phrase` or `prepositional_phrase`), then they will be highlighted together as a single phrase. This style breaks the highlighting between this word and the **_next_** word so that one phrase ends and another phrase begins.

    ![Separate Next Phrase Style](separate-next-phrase.png)

For Hybrid exemplars, words may have an additional property:
- _text_type_: Optional - If the word is highlighted as a text type (e.g. a dotted underline) on the text presentation screen, it should be given this property set to one of the values of the exemplar's   _additional_text_types_ field.

```json
{
    "text": "On Friday",
    "text_type": "Explanation"
}
```

![Additional Text Type Example](additional-text-type-example.png)

### Images

Images use the following schema:

- _type_: This is always "image"
- _editable_: This is an optional field that allows the image to be edited in the UI. It should be false for arrows and background graphics.
- _url_: The name of the file including extensions, e.g., "animals.jpg".

The image file should be supplied in the folder alongside the exemplar json file.

Images and sections in a panel need to be stored in the order shown on the text presentation screen:

```json
{
    "left": [
        {
            "type": "section",
            "label": "General Statement",
            "lines": []
        },
        {
            "type": "section",
            "label": "Description",
            "lines": []
        },
        {
            "type": "image",
            "editable": true,
            "url": "animals.jpg"
        }
    ],
    ...
}
```
# Contents
- [Specification](#specification)
- [Dependencies Title](#dependencies-title)

## Specification
Example text blah. Example text blah. Example text blah. Example text blah.
Example text blah. Example text blah. Example text blah. Example text blah.
Example text blah. Example text blah. Example text blah. Example text blah.
Example text blah. Example text blah.

## Dependencies Title
Example text blah. Example text blah. Example text blah. Example text blah.
Example text blah. Example text blah. Example text blah. Example text blah.
Example text blah. Example text blah. Example text blah. Example text blah.
Example text blah. Example text blah. 
_: For Hybrid exemplars, there will be additional text types associated. This should be an array of _text_type_ values.
- _collection_: The name of the collection to which this exemplar belongs. Examples include "Early A", "Early B".
- _order_: The order in which the exemplar appears in the book
- _thumbnail_: a relative path to the thumbnail image for the exemplar 

## Teacher Focus

The teacher_focus is an array that captures all the teacher focus notes at the top of each screen. Each object in the array has:

- _screen_: The name of the screen. This should be one of the following (case sensitive):
  - "Text Presentation"
  - "Text Structure"
  - "Language Features"
- _content_: The content of the teacher focus section saved as markdown. Please use line breaks for content over multiple lines. Please do not include content for "Access your Digital Exemplar here" or "Access more Explicit Teaching Strategies here" from this panel.

```json
{
    "screen": "Text Presentation",
    "content": "__Markdown__ content that _can_ include \nLine breaks."
},
{
    "screen": "Text Structure",
    "content": "__Markdown__ content that _can_ include \nLine breaks."
},
{
    "screen": "Language Features",
    "content": "__Markdown__ content that _can_ include \nLine breaks."
}
```

![Teacher Focus Example](teacher-focus.png)

## Section Labels

The section_labels is an array that captures the content explaining each of the sections on the text structure page. Each object in the array has:

- _label_: The name of the section shown in the darker coloured boxes.
- _description_: The description of the section shown in the lighter coloured boxes. This can be empty if the section doesn't have a description.

```json
{
    "label": "Title",
    "description": ""
},
{
    "label": "General Statement",
    "description": "What are the living or non-living things?"
},
```

![Section Labels Example](section-labels.png)

## Language Feature Labels

The language_feature_labels is an array that captures the content explaining each of the language features on the text structure page. Each object in the array has:

- _label_: The name of the language feature.

```json
{
    "label": "Nouns"
},
{
    "label": "Adjectives"
},
```

![Language Feature Labels Example](language-feature-labels.png)

Allowed language features labels:
- 'Nouns'
- 'Past-tense verbs'
- 'Time and sequence words'
- 'Adjectives'
- 'Present-tense verbs'
- 'Present-tense verbs (_to direct the reader_)'
- 'Present-tense relating verbs'
- 'Present-tense relating verbs (_is_, _are_, _has_, _have_)'
- 'Sensing verbs'
- 'Sensing verbs (_to describe feelings_)'
- 'Conjunctions'
- 'Conjunctions (_if_, _but_, _so_, _because_)'
- 'Conjunctions (_if_, _but_, _so_, _because_, _than_)'
- 'Conjunctions/Text connectives'
- 'Text connectives'
- 'Prepositional phrases'
- 'Phrases'
- 'Adverbs'

*Such language features as: 'Phrases' and 'Prepositional phrases' couldn't exist together, in one exemlar*
## Content

For Early Exemplars, the words and sentences across the different screens are the same, just displayed differently. So the content object must contain enough details to display the exemplar over all 3 screens.

The content is separated into `left` and `right` panels:

```json
{
    "content": {
        "left": [],
        "right": []
    }
}
```

Within each panel is an array that contains sections and/or images.

![Content Example](content-example.png)

Some exemplars may have content, such as an image, that spans both left and right panels at the bottom of the exemplar. In this situation a `bottom` panel can be included:

```json
{
    "content": {
        "left": [],
        "right": [],
        "bottom": []
    }
}
```

### Sections

Each section contains the text from the section block on the text structure page. The schema is as follows:

- _type_: This is always "section"
- _label_: Optional - The name of the section. If used, this **_must_** match a label in the section_labels array for the exemplar. If a section appears on both left and right panels, then the same label may be used. If the section is not labelled in the Text Structure screen, this may be omitted.
- _style_: Any special text styles for the section are mentioned here as an array of strings. This may contain any of the following values:
  - On a title section, include the value `"heading"`
  - On a section where text is right-aligned, include the value `"right-aligned"` 
- _color_: Optional - the colour of the text as displayed on the "Text Presentation" screen
- _lines_: An array of lines of text, which is explained below.

```json
{
    "type": "section",
    "label": "Title",
    "style": ["heading", "right-aligned"],
    "color": "A5D9EB",
    "lines": [
        ...
    ]
},
{
    "type": "section",
    "label": "General Statement",
    "lines": [
        ...
    ]
},
```

![Section Example](section-example.png)

### Sections, Lines and Words

Each section contains an array of lines, and each line contains an array of words:

```json
{
    "type": "section",
    "label": "General Statement",
    "lines": [
        {
            "words": [
                {
                    "text": "Show",
                    "language": "Nouns"
                },
                {
                    "text": "animals",
                    "language": "Nouns"
                },
                {
                    "text": "are",
                    "language": "Present-tense verbs"
                },
                {
                    "text": "animals",
                    "language": "Nouns"
                }
            ]
        },
        {
            "words": [
                {
                    "text": "that"
                },
                {
                    "text": "can",
                    "language": "Present-tense verbs"
                },
                {
                    "text": "win",
                    "language": "Present-tense verbs"
                },
                ...
            ]
        }
    ]
},
```

Each line uses the following schema:

- _words_: an array of word objects for the line
- _style_: this is an array, used for some styles applied to an entire line of words, such as `sub-heading`, `ordered-list` and `unordered-list`. These styles are only required for the [Procedure](procedure.md) text type. If not needed it can be excluded. 
- _sequence_number_: in the case of a line with an `ordered-list` style, this will store the number shown next to the line of words. If not needed it can be excluded.  

```json
{
    "words": [
        {
            "text": "Open"
        }
    ],
    "style": ["ordered-list"],
    "sequence_number": "3."
}
```

Each line must be a separate line object, even if it breaks a sentence into multiple lines.

Some sections may contain an empty line to separate two lines of text. These should be stored as a separate line object with an empty words array.

```json
{
    "words": []
}
```

![Empty Line Example](empty-line-example.png)

Each word uses the following schema:

- _text_: The word to be displayed on the page. **Notes:**
   - Please avoid storing space characters in the text property as it will lead to inconsistent spacing between words on the Language Features screen.
   - Please include apostrophes as part of the word text e.g. `That’s`.
   - Please store other punctuation characters (e.g. `,` `.` `!` `?` `“` `”`) as separate word objects.
- _text_type_: Optional - If the word is highlighted as a text type (e.g. a dotted underline) on the text presentation screen, it should be given this property set to the second value of . If unset, it will be assumed false.
- _language_: If the word is highlighted on the language features screen, it should be given a "language" value which **_must_** match a label in the language_feature_labels array for the exemplar. Otherwise, this should be excluded.
- _prepositional_phrase_: Optional - If the word is highlighted as a prepositional phrase (e.g. a dotted underline) on the language features screen, it should be given this property set to true. If unset, it will be assumed false. For Developing, Consolidating and Extending exemplars only.
- _phrase_: Optional - If the word is highlighted as a phrase (e.g. a solid underline) on the language features screen, it should be given this property set to true. If unset, it will be assumed false. For Extending exemplars only.
- _style_: Optional - This is used to apply bold/italics and other styles to words (see below), otherwise it can be excluded. These values cannot be repeated in the same array, like: *"style": ["bold", "bold"]*

```json
{
    "text": "Cows",
    "language": "Nouns",
    "prepositional_phrase": false,
    "phrase": false,
    "style": [
        "bold",
        "italic"
    ]
}
```

The following _style_ values may be applied to words:
- `"bold"`: Display the word with a bold font weight
- `"italic"`: Display the word with an italicised font style
- `"nospacing"`: A gap is normally added between words when they are displayed. This style removes the gap **_before_** the word object so that it is adjacent to the previous word. This is used:
   - on punctuation such as `,` `.` and `”` (closing quotes) so that there is no space between it and the previous word.

       !["nospacing" on Punctuation](word-nospacing-punctuation.png)
   - on a word **_after_** `“` (opening quotes) so that there is no space between the word an the quote marks.

       !["nospacing" on Following word](word-nospacing-word.png)
- `"separate-next"`: If two or more consecutive words have the same language feature, then they will be highlighted together as a single language feature. This style breaks the highlighting between this word and the **_next_** word so that they are highlighted as separate language features.

    ![Separate Next Style](separate-next.png)
- `"separate-next-phrase"`: Similar to `"separate-next"`, but for phrases. If two or more consecutive words have the same phrase (`phrase` or `prepositional_phrase`), then they will be highlighted together as a single phrase. This style breaks the highlighting between this word and the **_next_** word so that one phrase ends and another phrase begins.

    ![Separate Next Phrase Style](separate-next-phrase.png)

For Hybrid exemplars, words may have an additional property:
- _text_type_: Optional - If the word is highlighted as a text type (e.g. a dotted underline) on the text presentation screen, it should be given this property set to one of the values of the exemplar's   _additional_text_types_ field.

```json
{
    "text": "On Friday",
    "text_type": "Explanation"
}
```

![Additional Text Type Example](additional-text-type-example.png)

### Images

Images use the following schema:

- _type_: This is always "image"
- _editable_: This is an optional field that allows the image to be edited in the UI. It should be false for arrows and background graphics.
- _url_: The name of the file including extensions, e.g., "animals.jpg".

The image file should be supplied in the folder alongside the exemplar json file.

Images and sections in a panel need to be stored in the order shown on the text presentation screen:

```json
{
    "left": [
        {
            "type": "section",
            "label": "General Statement",
            "lines": []
        },
        {
            "type": "section",
            "label": "Description",
            "lines": []
        },
        {
            "type": "image",
            "editable": true,
            "url": "animals.jpg"
        }
    ],
    ...
}
```
# Contents
- [Specification](#specification)
- [Dependencies Title](#additiona_text_types)

## Specification
Example text blah. Example text blah. Example text blah. Example text blah.
Example text blah. Example text blah. Example text blah. Example text blah.
Example text blah. Example text blah. Example text blah. Example text blah.
Example text blah. Example text blah.

## Dependencies Title
Example text blah. Example text blah. Example text blah. Example text blah.
Example text blah. Example text blah. Example text blah. Example text blah.
Example text blah. Example text blah. Example text blah. Example text blah.
Example text blah. Example text blah. 
