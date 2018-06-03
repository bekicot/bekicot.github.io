---
layout: post
title: "Git: The Trailing Comma Journey"
date: 2018-06-03T19:24:51+07:00
category: GSoC-2018
---

## Comma
Comma `U+002C` in programming language, usually used to separating each item of
a list or a hash. The common usage in programming language is to place `comma`
in between item on a list. e.g:

```
fruits = ['apple', 'banana', 'mango']
```

In Ruby, Python, and JavaScript the syntax above is valid. But for list with
item that has a long name. Locating a specific item will be tedious.
Another way to format it is by separating each item into separate line.

```
fruits = [
  'apple',
  'banana',
  'mango'
]
```
With this format, secifying an item is easy, especially if the item is sorted.
The downside of this format is if we want to add new item, we requires edit 2
lines, the first 1 is adding comma at the end of the last item ('Manggo'). Then
adding a new item itself in new line.

## New Item of an Array and Git
For Git, the new Item will add unnecessary changes in the last item of the list.
The solution of this is to adding a trailing comma to the last item of the list.

```
fruits = [
  'apple',
  'banana',
  'mango',
]
```

## Enforce Trailing Comma
We can enforce this style using a linter, on eslint you can specify
`comma-dangle` config:
```
{
    "rules": {
      "comma-dangle": ["error", {
        "arrays": "always-multiline",
        "objects": "always-multiline",
      }]
    }
}
```

This will raises error if there is a multiline array or hash that doesn't have
a trailing comma.

## Coala Pull Request with this issue

- https://github.com/coala/landing-frontend/pull/278