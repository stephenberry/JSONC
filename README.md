# JSONC
JSON with Comments. This is a simple reference specification for JSONC.

JSONC makes JSON documents more useful for humans and avoids embedding comments as part of the JSON document, which hurts performance and clarity.

JSONC allows C and Javascript style comments. When a JSONC document is read, all comments must be ignored and the result is a JSON structure identical to a JSONC document with all the comments stripped.

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

