---
description: Used to identify a schema containing definitions of types that are referred to in the stylesheet
---

# xsl:import-schema

Used to identify a schema containing definitions of types that are referred to in the stylesheet.

_Available in XSLT 2.0 and later versions. Requires Saxon-EE._

- **Category**: declaration
- **Content**: `xs:schema?`
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-transform.md)

## Attributes

`namespace?`
: _uri_
: Specifies the target namespace of the schema to be imported. The attribute should be omitted when importing a schema with no target namespace.

`schema-location?`
: _uri_
: Specifies where the schema document can be found. This URI is passed through the `URIResolver` in the same way as the URIs used on [`xsl:include`](xsl-include.md) and [`xsl:import`](xsl-import.md). The attribute can be omitted only if a schema for the required namespace has already been loaded in the `Configuration`, for example if it has already been imported from another stylesheet module.

## Notes on the Saxon implementation

The `xsl:import-schema` declaration requires a schema-aware processor, so is only available in Saxon-EE. For further information see Schema Processing.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-import-schema)
- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-import-schema)
- [Saxon](http://www.saxonica.com/documentation/index.html#!xsl-elements/import-schema)

## See also

- [`xsl:include`](xsl-include.md)
- [`xsl:import`](xsl-import.md)
