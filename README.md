# EON-Markup

_A markup language for the XXIVth century_

_yeah dude_

![Preview](https://github.com/botbreeder/eon-markup/raw/main/img/Sector0x00.png)

## Preview

EON-Markup is a markup language you can use to annotate text with data. Here is how it looks like.

```
this is a [tagged]Hello World[/tagged] example
```

And here is the JSON representation of this example.

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
