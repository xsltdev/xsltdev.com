---
description: The xsl stylesheet element is always the top-level element of an XSLT stylesheet
---

# xsl:stylesheet

The **`xsl:stylesheet`** element is always the top-level element of an XSLT stylesheet. The name [`xsl:transform`](xsl-transform.md) may be used as a synonym.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Content**: _( declarations )_

## Attributes

`id?`
: _id_
: Used to reference stylesheet modules embedded in a document.

**`version`**
: _decimal_
: Standard attribute that may appear on any XSLT element. Indicates the version of XSLT required by the stylesheet.

: To request XLST 3.0 processing (which requires Saxon-PE or Saxon-EE), setting `version="3.0"` on the `xsl:stylesheet` element is recommended, but is not sufficient on its own. An explicit request must be made on the command line or by the API. Using the XSLT 3.0 processor, a value greater than 3.0 invokes forwards compatibility mode.

: When using the XSLT 2.0 processor (in particular, using Saxon-HE), a value greater than `2.0` invokes forwards compatibility mode.

`default-mode?`
: `eqname | "#unnamed"`
: Standard attribute that may appear on any XSLT element. Defines the default value for the mode attribute of all [`xsl:template`](xsl-template.md) and [`xsl:apply-templates`](xsl-apply-templates.md) elements within its scope.

`default-validation?`
: `"preserve" | "strip"`
: Standard attribute that may appear on any XSLT element. Defines the default value for the `validation` attribute of all relevant instructions appearing within its scope. The default is `strip`.

`input-type-annotations?`
: `"preserve" | "strip" | "unspecified"`
: Used to request stripping of type annotations. The default is `unspecified`.

`default-collation?`
: `uris`
: Standard attribute that may appear on any XSLT element. Specifies the default collation used by all XPath expressions appearing in attributes or text value templates within its scope (unless overridden by another `default-collation` attribute on a descendant); and used by certain XSLT constructs within its scope. If present it must be a whitespace-separated list of collation URIs, that use the scheme and path `http://www.w3.org/2013/collation/UCA` (to request use of the Unicode Collation Algorithm), or collations otherwise recognized by Saxon (see Collation).

`extension-element-prefixes?`
: _prefixes_
: Standard attribute that may appear on any XSLT element. Used to declare the use of extension instructions in a particular namespace.

`exclude-result-prefixes?`
: _prefixes_
: Standard attribute that may appear on any XSLT element. Used to designate namespaces as excluded.

`expand-text?`
: _boolean_
: Standard attribute that may appear on any XSLT element. New in XSLT 3.0, and Saxon 9.5. If set to `yes`, enables the use of text _value templates_ - expressions enclosed in curly braces within text nodes, behaving the same way as attribute value templates in attribute nodes - for descendant text nodes (unless overridden by another `expand-text` attribute on a descendant). The default is `no`.

`use-when?`
: _expression_
: Standard attribute that may appear on any XSLT element. Used to conditionally include or exclude elements. The value is an XPath expression that can be evaluated statically. If the effective boolean value is false, then the element and all its descendants are effectively excluded from the stylesheet module.

`xpath-default-namespace?`
: _uri_
: Standard attribute that may appear on any XSLT element. Determines the namespace used for any unprefixed element name or type name within an XPath expression. The value may be overridden by another `xpath-default-namespace` attribute on a descendant. The default is a zero-length string, for names in no namespace.

`saxon:explain?`
: boolean
: Saxon attribute that may appear on any XSLT element. If the value is `yes`, then at compile time Saxon outputs (to the standard error output) a representation of the optimized expression tree for the template or function containing that instruction.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-stylesheet)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-stylesheet)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/stylesheet)

## See also

- [`xsl:transform`](xsl-transform.md)
- [`xsl:package`](xsl-package.md)
