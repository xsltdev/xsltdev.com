---
description: Used to include the contents of one stylesheet within another
---

# xsl:include

Used to include the contents of one stylesheet within another.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: declaration
- **Content**: none
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-transform.md)

## Attributes

**`href`**
: uri
: A URL (absolute or relative) of another stylesheet to be textually included within this one.
: To customize the way in which the href attribute is handled, a user-written `URIResolver` can be supplied (or on .NET, an `XMLResolver`). Note that it is the compile-time `URIResolver` that is used, not the run-time `URIResolver`.
: If the URI is relative, then it is interpreted relative to the base URI of the `xsl:include` element itself, which normally is the location of the file containing the source stylesheet module. If the stylesheet is loaded other than from a file (for example, if it is supplied as a string literal in the source of the application program that invokes the transformation), then a base URI should be supplied when invoking the compilation.

## Details

The `xsl:include` element is always used at the top level of the stylesheet. The top-level elements of the included stylesheet effectively replace the `xsl:include` element.

The `xsl:include` element may also be used at the top level of the included stylesheet, and so on recursively.

("Textual inclusion" here is a simplification: attributes and namespaces declared on the [`xsl:stylesheet`](xsl-stylesheet.md) element of the including module do not affect anything in the included module.)

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-include)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-include)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/include.html)

## See also

- [`xsl:import`](xsl-import.md)
