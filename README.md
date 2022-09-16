# EON-Markup

_A markup language for the time-traveling space monkeys from the XXIVth century_

_Are we running in circles? yeah_

![Preview](https://github.com/botbreeder/eon-markup/raw/main/img/Sector0x00.png)

## Preview

EON-Markup is a markup language you can use to annotate text with data. Here is how it looks like.

```
this is a [tagged]Hello World[/tagged] example
```

And here is the JSON representation of this example, as returned by the reference parser you can download from this repo.

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

In this version, the opening tag is a legal JSON array.

![Overview](https://github.com/botbreeder/eon-markup/raw/main/img/Sector0x01.png)

## Overview

Like XML, EON-Markup is a markup language that can be used to create annotated and structured documents. The differences are:

- The opening tags of XML elements can contain attributes, which are key-value pairs.
- The opening tags of EON elements can be **JSON arrays** or **JSON objects**.
- XML has a clear spec, a jumanjiesque ecosystem, a Wikipedia article and [XSLT](https://en.m.wikipedia.org/wiki/XSLT).
- EON-Markup is a tiny shithack in a dark corner of github. With cool banners though.

**Why should I care?**

You shouldn't, but if you do, you're getting a nobrain tool of great capabilities. An EON-M document can be as simple as a straight JSON object, or as complex as a human thought and still easy on the eye. Instead of simple key-value pairs, you have the full power of JSON directly in your document tags.

**What's the use case?**

Its initial purpose is to be a _lingua franca_ for chatbots' inter-organ communication. But I believe you can do a lot of powerful things with this baby like, processing grocery lists and, stuff. You know, it's Turing-responsive™ so yeah, very cool.

![Overview](https://github.com/botbreeder/eon-markup/raw/main/img/Sector0x02.png)

## Superset

EON-Markup accepts a superset of JSON.

### Identifiers

Strings can be delimited by double quotes, as usual, or they can be identifiers.

- An identifier is not between double quotes.
- An identifier can begin with a digit.
- An identifier cannot contain whitespaces.
- An identifier can contain anything but `[ ] { } : , " / \` 

An identifier is always converted to a regular string, unless it can be parsed as a number.

You can use identifiers as keys and as values, which means the following document is legal.

```
some {size:big}text{/size} identifier example
```

### Lists

Commas are mandatory in objects, but they can be omitted in arrays.

```
[1 2 3D foo] ok [/]

[1, 2, "3D", "foo"] ok [/]
```

Those 2 lines above are the exact same thing: an array of 4 items, 2 numbers and 2 strings.

![Closing](https://github.com/botbreeder/eon-markup/raw/main/img/Sector0x10.png)

## Closing

EON-Markup is not strict on the shape of closing tags.

### Arrays

For an array tag, like `[foo]`, the closing tag is `[/id]` where `id` can be any identifier or nothing. There's a forward slash immediately following the opening bracket of the closing tag. The examples below are legal.

```
[foo] example [/foo]
[foo] example [/f]
[foo] example [/]
[foo] example [/bar]
```

The 4th example above is as legal as the others. It shows that you can really use _any_ identifier. You're in charge, so don't make poor choices.

### Objects

Same goes for object tags. For a tag like `{foo:mew}`, the closing tag is `{/id}` where `id` can be any identifier or nothing. There's a slash just after the opening brace of the closing tag. These examples are legal.

```
{foo:mew} example {/foo}
{foo:mew} example {/f}
{foo:mew} example {/}
{foo:mew} example {/mew}
{foo:mew} example {/bar}
```

The 5th example above shows that you can really use _any_ identifier. Again, you're in charge, don't make poor choices.

### Void

Void elements are elements without content. `[empty/]` is syntactic sugar for `[empty][/]`.

![Usage](https://github.com/botbreeder/eon-markup/raw/main/img/Sector0x11.png)

## Usage

### PEGjs

You can generate the parser yourself, using the syntax in [PEGjs-syntax.txt](https://github.com/botbreeder/eon-markup/blob/main/PEGjs-syntax.txt) on the [Online version of PEGjs](https://pegjs.org/online).

### Nodejs

You can require [eon-parser-module.js](https://github.com/botbreeder/eon-markup/blob/main/eon-parser-module.js) which exports the parser.

### Browser

You can use [eon-parser.js](https://github.com/botbreeder/eon-markup/blob/main/eon-parser.js) which exposes a `EONParser` object, or [eon-parser-module.js](https://github.com/botbreeder/eon-markup/blob/main/eon-parser-module.js) which exports the parser.

```HTML
<!DOCTYPE html>
<html>

<head>
    <title>EON-Markup</title>
    <style>
        body {
            font-family: monospace;
            white-space: pre;
            color: white;
            background: black;
        }
    </style>
</head>

<body>
<script src="eon-parser.js"></script>
<script>
    document.write(
        JSON.stringify(
            EONParser.parse(`[+ 2 3 4]come on[/] babe`),
            null,
            4
        )
    );
</script>
</body>

</html>
```

![NAQ](https://github.com/botbreeder/eon-markup/raw/main/img/Sector0x12.png)

## NAQ

### _What are NAQ?_

NAQ are Never Asked Questions.

### _How do I escape braces and brackets?_

You can use a backslash `\` to escape any character, like `{`, `[`, or `\`.

| Escape sequence | Result |
|-----------------|--------|
| \\{              | {      |
| \\[              | [      |
| \\\\              | \      |

### _Why's this question unanswered?_







