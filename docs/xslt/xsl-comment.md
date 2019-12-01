---
description: Indicates text that is to be output to the current output stream in the form of an XML or HTML comment
---

# xsl:comment

Indicates text that is to be output to the current output stream in the form of an XML or HTML comment.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: sequence-constructor
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

`select?`
: _expression_
: The content of the comment may be given either by a `select` attribute or by an enclosed sequence constructor. If the `select` attribute is used and the value is a sequence, then the items in the sequence are output space-separated.

## Details

The `xsl:comment` element can appear anywhere within an [`xsl:template`](xsl-template.md).

Note that special characters occurring within the comment text will _not_ be escaped.

The `xsl:comment` element will normally contain text only but it may contain other elements such as [`xsl:if`](xsl-if.md) or [`xsl:value-of`](xsl-value-of.md). However, it should not contain literal result elements.

_Tip: the `xsl:comment` element can be very useful for debugging your stylesheet. Use comments in the generated output as a way of tracking which rules in the stylesheet were invoked to produce the output._

In XSLT 3.0, it is often convenient to construct comments using text value templates, for example `<xsl:comment expand-text='yes'>Status: {$status}</xsl:comment>`.

## Examples

The text below inserts some JavaScript into a generated HTML document:

```html
<script language="JavaScript">
  <xsl:comment>
      function bk(n) {
          parent.frames['content'].location="chap" + n + ".1.html";
      }
  //</xsl:comment>
</script>
```

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-comment)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-comment)
- [Saxon](http://www.saxonica.com/documentation/index.html#!xsl-elements/comment)
