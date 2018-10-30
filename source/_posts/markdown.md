---
layout: post
title: Markdown语法参考
date: 2016-03-03
categories: [general]
tags: [life]
fullview: 
shortinfo: 
description: Markdown语法
---

# Standard Markdown

## Strong and Emphasize

```
*emphasize*   **strong**
_emphasize_   __strong__
```

## Links and Email

```
An [example](http://url.com/ "Title")
```
```
An [example][id]. Then, anywhere
else in the doc, define the link:

[id]: http://example.com/  "Title"
```
Email:

```
An email <example@example.com> link.
```

## Images

```
![alt text](/path/img.jpg "Title")
```

```
![alt text][id]

[id]: /url/to/img.jpg "Title"
```

## Headers

```
Setext-style:

Header 1
========

Header 2
--------
```

atx-style (closing #’s are optional):

```
# Header 1 #

## Header 2 ##

###### Header 6
```

## Lists
Ordered, without paragraphs:

```
1.  Foo
2.  Bar
```

Unordered, with paragraphs:

```
*   A list item.

    With multiple paragraphs.

*   Bar
```

You can nest them:

```
*   Abacus
    * answer
*   Bubbles
    1.  bunk
    2.  bupkis
        * BELITTLER
    3. burper
*   Cunning
```

## Blockquotes

```
> Email-style angle brackets
> are used for blockquotes.

> > And, they can be nested.

> #### Headers in blockquotes
> 
> * You can quote a list.
> * Etc.
```

## Inline Code

```
`<code>` spans are delimited
by backticks.

You can include literal backticks
like `` `this` ``.
```

## Block Code

Indent every line of a code block by at least 4 spaces or 1 tab.

```
This is a normal paragraph.

    This is a preformatted
    code block.
```

## Horizontal Rules

Three or more dashes or asterisks:

```
---

* * *

- - - -
```

## Hard Line Breaks

End a line with two or more spaces:

```
Roses are red,   
Violets are blue.
```

## Table

```
| A | B | C |
| --- |:---:|  ---:|
| 1111111111111111111 | 222222222222222222222 | 33333333333333333 |
```
## Code

|Python |Ruby |Haml |Perl|PHP |Scala|Go|XML|HTML|Lasso|Markdown|AscllDoc|
|Django|Handlebars|CSS|SCSS|JSON|JavaScript|CoffeScript|ActionScript|VBScript|
|VB.NET|HTTP|Lua|AppleScript|Delphi|Oxygene|Java|C++|objectivec|Vala|C#|
|F#|OCaml|D|rsl|rib|MEL|GLSL|SQL|SmallTalk|Lisp|Clojure|
|ini|Apache|nginx|Diff|dos|bash|makefile|cmake|axapta|ruleslanguage|
|1c|avrasm|vhdl|parser3|livecodeserver|tex|brainfuck|haskell|erlang|
|erlang-repl|rust|matlab|scllab|r|mizar|mathematica|autohotkey|fix| 　