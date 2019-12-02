---
description: Used to modify the visibility of selected components within a package
---

# xsl:expose

Used to modify the visibility of selected components within a package.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.7._

- **Content**: none
- **Permitted parent elements**: [`xsl:package`](xsl-package.md)

## Attributes

**`component`**
: `"template" | "function" | "attribute-set" | "variable" | "mode" | "*"`
: Identifies the kind of component that is selected.

**`names`**
: _tokens_
: Identifies a subset of the specified components, by name.

**`visibility`**
: `"public" | "private" | "final" | "abstract"`
: Determines the external visibility of the selected components.

## Notes on the Saxon implementation

New in XSLT 3.0, and implemented since Saxon 9.7.

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-expose)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/expose)

## See also

- [`xsl:package`](xsl-package.md)
