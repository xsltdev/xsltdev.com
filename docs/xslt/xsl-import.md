---
description: Used to import the contents of one stylesheet module into another
---

# xsl:import

Used to import the contents of one stylesheet module into another.

Available in XSLT 1.0 and later versions. Available in all Saxon editions.

- **Category**: declaration
- **Content**: none
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-transform.md)

## Attributes

**`href`**
: _uri_
: A URL (absolute or relative) of another stylesheet to be textually included within this one.
: To customize the way in which the href attribute is handled, a user-written `URIResolver` can be supplied. Note that it is the compile-time `URIResolver` that is used, not the run-time `URIResolver`.
: If the URI is relative, then it is interpreted relative to the base URI of the `xsl:import` element itself, which normally is the location of the file containing the source stylesheet module. If the stylesheet is loaded other than from a file (for example, if it is supplied as a string literal in the source of the application program that invokes the transformation), then a base URI should be supplied when invoking the compilation.

## Notes on the Saxon implementation

XSLT 3.0 removes the restriction that `xsl:import` elements must precede all others in the stylesheet. Since Saxon 9.5 this restriction was removed provided that XSLT 3.0 is enabled; in Saxon 9.8 it was removed entirely.

## Details

The `xsl:import` element is always used at the top level of the stylesheet. In XSLT 2.0 it must appear before all other elements at the top level, but XSLT 3.0 removes this restriction. The top-level elements of the included stylesheet effectively replace the `xsl:import` element.

The `xsl:import` element may also be used at the top level of the included stylesheet, and so on recursively.

The elements in the imported stylesheet have lower precedence than the elements in the importing stylesheet. The main effect of this is on selection of a template when [`xsl:apply-templates`](xsl-apply-templates.md) is used: if there is a matching template with precedence X, all templates with precedence less than X are ignored, regardless of their priority.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-import)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-import)
- [Saxon](http://www.saxonica.com/documentation/index.html#!xsl-elements/import)

## See also

- [`xsl:apply-imports`](xsl-apply-imports.md)
- [`xsl:apply-templates`](xsl-apply-templates.md)
- [`xsl:include`](xsl-include.md)
