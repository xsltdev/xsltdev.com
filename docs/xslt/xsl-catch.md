---
description: In conjunction with xsl try, the xsl catch instruction allows recovery from dynamic errors
---

# xsl:catch

In conjunction with [`xsl:try`](xsl-try.md), the **`xsl:catch`** instruction allows recovery from dynamic errors.

Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.6.

- **Content**: _sequence-constructor_
- **Permitted parent elements**: [`xsl:try`](xsl-try.md)

## Attributes

`errors?`
: _tokens_
: Indicates which error codes are caught. If absent, or if set to `*`, all errors are caught. The value can be a whitespace-separated list of QNames; the wildcards `*:local or prefix:*` can also be used.

`select?`
: _expression_
: The effect of the element may be defined either by a `select` attribute, or by an enclosed sequence constructor.

## Details

It is possible to have more than one `xsl:catch` within an [`xsl:try`](xsl-try.md); the first one that matches the error is used.

Within the `xsl:catch`, a number of variables are available in the namespace `http://www.w3.org/2005/xqt-errors`:

- `err:code` - the error code as a QName
- `err:description` - the error description (error message)
- `err:value` - the error object (if available)
- `err:module` - the URI of the stylesheet module in which the error occurred
- `err:line-number` - the line-number of the source stylesheet where the error occurred
- `err:column-number` - for Saxon this will generally be unknown (-1)

The error can be re-thrown by using the `error()` function.

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-catch)
- [Saxon](http://www.saxonica.com/documentation/index.html#!xsl-elements/catch)

## See also

- [`xsl:try`](xsl-try.md)
