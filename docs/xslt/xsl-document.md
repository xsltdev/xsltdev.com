---
description: Creates a new document node
---

# xsl:document

Creates a new document node.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

`validation?`
: `"strict" | "lax" | "preserve" | "strip"`
: Used to perform document-level validation. Requires Saxon-PE or Saxon-EE.

`type?`
: _eqname_
: Determines what happens to any type annotations on element or attribute nodes. Requires Saxon-PE or Saxon-EE.

## Notes on the Saxon implementation

This instruction should not be confused with the instruction of the same name in the withdrawn XSLT 1.1 draft, (which is supported in Saxon 6.5.x). That instruction was a precursor to [`xsl:result-document`](xsl-result-document.md).

## Details

The content of the new document node is created using the contained instructions (in the same way as `xsl:result-document`), and the new document node is added to the result sequence. The instruction is useful mainly if you want to validate the document: the element allows attributes `validation` and `type` which perform document-level validation in the same way as the corresponding attributes on `xsl:result-document`.

The instruction also allows a function or template to create a temporary tree without the need to create a variable and then return the value of the variable.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-document)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-document)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/document)

## See also

- [`xsl:result-document`](xsl-result-document.md)
