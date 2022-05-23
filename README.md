# JSONC
JSON with Comments. This is a simple explanation of the specification.

JSONC allows C, C++, or Javascript style comments, all of which are the same.

> `.jsonc` is the standard file extension for JSONC

## Line Comments

Single line comments use double forward slashes `//` and the comment continues to the end of the line even if there are new comment symbols.

```jsonc
{
  "x": 5 // this is a line comment
}
```

## Block Comments

Block comments support in place commenting and multi-line comments.

```jsonc
/*
Here is a block comment.
This can span multiple lines.
*/
{
  "key": /*An in place comment*/ "a string"
}
```

JSONC restricts their usage to outside of strings. Within strings they are considered part of the string.

```json
{
	"Key": "One upon /*This comment is part of the string*/ a time"
}
```

