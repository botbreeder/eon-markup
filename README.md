# EON-Markup

_A markup language for the space dudes from the XXIVth century_

_Are we running in circles? yeah_

![Preview](https://github.com/botbreeder/eon-markup/raw/main/img/Sector0x00.png)

## Preview

EON-Markup is a markup language you can use to annotate text with data. Here is how it looks like.

```
this is a [tagged]Hello World[/tagged] example
```

And here is the JSON representation of this example, as returned by the official parser.

```JSON

[
   {
      "tag": "none",
      "content": "this is a "
   },
   {
      "tag": "array",
      "array": [
         "tagged"
      ],
      "content": [
         {
            "tag": "none",
            "content": "Hello World"
         }
      ]
   },
   {
      "tag": "none",
      "content": " example"
   }
]

```

The same could be written like this:

```
this is a [tagged]Hello World[/] example
```

... or like this:


```
this is a ["tagged"]Hello World[/] example
```

... where the opening tag is a legal JSON array.

![Overview](https://github.com/botbreeder/eon-markup/raw/main/img/Sector0x01.png)

## Overview

Like XML, EON-Markup is a markup language that can be used to create annotated and structured documents. The differences are:

- The opening tags of an XML element can contain attributes, which are key-value pairs.
- The opening tags of an EON element can be JSON arrays or JSON objects.
- XML has a clear spec, a jumanjiesque ecosystem, a Wikipedia article and XSLT.
- EON-Markup is a tiny shithack in a dark corner of github. With cool banners though.

Why should I care?

You shouldn't, but if you do, you're getting a nobrain tool of great capabilities. An EON-M document can be as simple as a straight JSON object, or as complex as a human thought and still easy on the eye. Instead of simple key-value pairs, you have the full power of JSON directly in your document tags.

Eon-Markup accepts a superset of JSON. Strings can be delimited by double quotes, as usual, or they can be identifiers: `[a-zA-Z_][0-9a-zA-Z_]*`
