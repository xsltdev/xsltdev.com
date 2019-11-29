---
description: Allows a package to restrict the visibility of components exposed by a package that it uses
---

# xsl:accept

Allows a package to restrict the visibility of components exposed by a package that it uses.

Always appears as a child of [`xsl:use-package`](xsl-use-package.md).

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-EE since Saxon 9.7._

- **Content**: none
- **Permitted parent elements**: [`xsl:use-package`](xsl-use-package.md)

## Attributes

**`component`**
: `"template" | "function" | "attribute-set" | "variable" | "mode" | "*"`
: Identifies the kind of component selected.

**`names`**
: _tokens_
: Identifies a subset of the specified components, by name.

**`visibility`**
: `"public" | "private" | "final" | "abstract" | "hidden"`
: Determines the potential visibility of the selected components.

## Notes on the Saxon implementation

New in XSLT 3.0, and implemented since Saxon 9.7.

## Links to W3C specifications

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-accept)

## See also

- [`xsl:override`](xsl-override.md)
- [`xsl:use-package`](xsl-use-package.md)
