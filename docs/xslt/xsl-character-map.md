---
description: Defines a named character map for use during serialization
---

# xsl:character-map

Defines a named character map for use during serialization.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: declaration
- **Content**: ( [`xsl:output-character`](xsl-output-character.md)\* )
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-transform.md)

## Attributes

**`name`**
: _eqname_
: The name of the character map, which can be referenced from the `use-character-maps` attribute of [`xsl:output`](xsl-output.md).

`use-character-maps?`
: _eqnames_
: Character maps may be assembled from other character maps using the `use-character-maps` attribute. This contains a space-separated list of the names of other character maps that are to be included in this character map.

## Notes on the Saxon implementation

Using character maps may be expensive at run-time. Saxon currently makes no special attempts to optimize their use: if character maps are used, then every character that is output will be looked up in a hash table to see if there is a replacement string.

Saxon 9.8 extends the use of character maps so they also apply to the JSON output method. For example, a character map that maps `"/"` to `"/"` will prevent the JSON output method escaping `"/"` as `"\/"`.

## Details

The `xsl:character-map` element contains a set of [`xsl:output-character`](xsl-output-character.md) elements each of which defines the output representation of a given Unicode character. The character is specified using the `character` attribute, the string which is to replace this character on serialization is specified using the `string` attribute. Both attributes are mandatory.

The replacement string is output _as is_, even if it contains special (markup) characters. So, for example, you can define `<xsl:output-character character="&#xa0;" string="&nbsp;"/>` to ensure that NBSP characters are output using the entity reference `&nbsp;`.

Character maps allow you to produce output that is not well-formed XML, and they thus provide a replacement facility for `disable-output-escaping`. A useful technique is to use characters in the Unicode private use area (xE000 to xF8FF) as characters which, if present in the result tree, will be mapped to special strings on output. For example, if you want to generate a proprietary XML-like format that uses tags such as `<!IF>`, `<!THEN>`, and `<!ELSE>`, then you could map these to the three characters xE000, xE001, xE002 (which you could in turn define as entities so they can be written symbolically in your stylesheet or source document).

Character maps are preferred to `disable-output-escaping` because they do not rely on an intimate interface between the transformation engine and the serializer, and they do not distort the data model. The special characters can happily be stored in a DOM, passed across the SAX interface, or manipulated in any other way, before finally being rendered by the serializer.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-character-map)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-character-map)
- [Saxon](http://www.saxonica.com/documentation/index.html#!xsl-elements/character-map)

## See also

- [`xsl:output`](xsl-output.md)
- [`xsl:output-character`](xsl-output-character.md)
