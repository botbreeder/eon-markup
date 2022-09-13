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

Like XML, EON-Markup is a markup language that can be used to create annotated and structured documents. The difference is:

- The opening tags of an XML element can contain attributes, which are key-value pairs.
- The opening tags of an EON element can be JSON arrays or JSON objects.
