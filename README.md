# JSONC
This document explains JSON with Comments. It aims to be a simple reference specification for JSONC. JSONC is a format based on JSON but with some small features and more lenient parsing behaviors, which are specified below.

**Why JSONC?** JSONC makes JSON documents more useful for humans and avoids embedding comments as part of the JSON document, which hurts performance and clarity. The main feature of JSONC is that it allows C and Javascript style comments. When a JSONC document is read, when all comments are ignored it usually leads to a JSON structure identical to a JSONC document with all the comments stripped.

> [!NOTE]
> `.jsonc` is the standard file extension for JSONC

## Line Comments

Single line comments use double forward slashes `//` and the comment continues to the end of the line even if there are new comment symbols.

```jsonc
{ "x": 5 // this is a line comment
}
```

## Block Comments

Block comments support in place commenting and multi-line comments.

```jsonc
/*
Here is a block comment.
This can span multiple lines.
*/
{ "key": /*An in place comment*/ "a string" }
```

JSONC restricts their usage to outside of strings (and therefore keys). Within strings they are considered part of the string.

```json
{ "Key": "One upon /*This comment is part of the string*/ a time",
  "Example": "Another example //of comment syntax as part of a string",
  "A /*key with comment syntax*/": "The key contains the comment"
}
```

Additionally, just like in C and C++, nested block comments are invalid.
```json
/* /* This does not work */ The first comment close sequence closes the outer comment */
```

## Trailing commas

JSONC usually supports trailing commas for use in config files, although
some implementations may not accept them or cause warnings. Inside a json object
(a key value object) or a json array (a list), a trailing comma can be used in
supprting implementations like this:

```json
{"Key1": "Value1",
 "Key2": "Value2",
}
```
Or like this:
```
[
1, 2,
3, 4,
]
```
