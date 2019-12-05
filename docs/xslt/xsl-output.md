---
description: Used to control the format of serial output files resulting from the transformation
---

# xsl:output

Used to control the format of serial output files resulting from the transformation.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: declaration
- **Content**: none
- **Permitted parent elements**: [`xsl:package`](xsl-package.md); [`xsl:stylesheet`](xsl-stylesheet.md); [`xsl:transform`](xsl-transform.md)

## Attributes

`name?`
: _eqname_
: Provides a name for this output format, which may be referenced in the [`xsl:result-document`](xsl-result-document.md) element. By default, the unnamed output format is used.

`method?`
: `"xml" | "html" | "xhtml" | "text" | "json" | "adaptive"` | _eqname_
: Indicates the format or destination of the output. The value xml indicates XML output (though if disable-output-escaping or character maps are used there is no guarantee that it is well-formed). A value of `html` is used for HTML output, and `xhtml` for XHTML. The value `text` indicates plain text output: in this case no markup may be written to the file using constructs such as literal result elements, [`xsl:element`](xsl-element.md), [`xsl:attribute`](xsl-attribute.md), or [`xsl:comment`](xsl-comment.md). Alternatively output can be directed to a user-defined Java program by specifying the name of the class as the value of the method attribute, prefixed by a namespace prefix, for example `xx:com.me.myjava.MyEmitter`. The class must be on the classpath, and must implement either the `org.xml.sax.ContentHandler` interface, or the `Receiver` interface. The last of these, though proprietary, is a richer interface that gives access to additional information. The value `json` is used for JSON output, and `adaptive` for _Adaptive_ output (these options are available in XPath 3.1, and implemented since Saxon 9.7).

`allow-duplicate-names?`
: _boolean_
: Used only for JSON output, available in XPath 3.1, implemented since Saxon 9.7. Defines whether duplicate keys (e.g. the date `2014-10-01` and the string `"2014-10-01"`, which have the same string value) are allowed in a JSON map. The value yes indicates that such duplicate keys will result in duplicate object-member names in the JSON output; whereas the value no indicates that such duplicates are an error.

`build-tree?`
: _boolean_
: Defines whether the raw output is used to build an XML document tree.

`byte-order-mark?`
: _boolean_
: Indicates whether UTF-8/UTF-16 output is to start with a byte order mark. The default is no.

`cdata-section-elements?`
: _eqnames_
: Used only for XML output. The value is a whitespace-separated list of element names. Character data belonging to these output elements will be written within CDATA sections.

`doctype-public?`
: _string_
: Used only for XML output: it is copied into the DOCTYPE declaration as the public identifier. Ignored if there is no system identifier. If the value is an empty string, Saxon interprets this as if the attribute were omitted, which can be useful it you want to override an actual value with "absent".

`doctype-system?`
: _string_
: Used only for XML output: it is copied into the DOCTYPE declaration as the system identifier. If the value is an empty string, Saxon interprets this as if the attribute were omitted, which can be useful it you want to override an actual value with "absent".

`encoding?`
: _string_
: A character encoding, e.g. `iso-8859-1` or `utf-8`. The value must be one recognised both by the Java run-time system and by Saxon itself: the encoding names that Saxon recognises are `ASCII`, `US-ASCII`, `iso-8859-1`, `utf-8`, `utf8`, `KOI8R`, `cp1251`. It is used for three distinct purposes: to control character conversion by the Java I/O routines; to determine which characters will be represented as character entities; and to document the encoding in the output file itself. The default (and fallback) is `utf-8`.

`escape-uri-attributes?`
: _boolean_
: New in XSLT 2.0. Affects HTML output only. Controls whether non-ASCII characters in HTML URI-valued attributes (for example, href) are escaped using the %HH convention. The default is `yes`.

`html-version?`
: _decimal_
: New in XSLT 3.0. Implemented since Saxon 9.6. When the output method is HTML or XHTML, then if this attribute takes decimal value 5.0, then the output produced is HTML 5.0 or XHTML 5.0 respectively.

`include-content-type?`
: _boolean_
: New in XSLT 2.0. Affects HTML output only. Controls whether a meta tag is inserted into the HTML head element. The default is `yes`.

`indent?`
: _boolean_
: The indentation algorithm is different for HTML and XML. For HTML it avoids outputting extra space before or after an inline element, but will indent text as well as tags, except in elements such as `PRE` and `SCRIPT`. For XML, it avoids outputting extra whitespace except between two tags. The emphasis is on conformance rather than aesthetics!

`item-separator?`
: _string_
: Not available in XSLT.

`json-node-output-method?`
: `"xml" | "html" | "xhtml" | "text"` | _eqname_
: Used only for JSON output, available in XPath 3.1, implemented since Saxon 9.7. Defines the serialization method for nodes encountered while serializing as JSON.

`media-type?`
: string
: For example, `text/xml` or `text/html`. This is largely documentary. However, the value assigned is passed back to the calling application in the `OutputDetails` object, where it can be accessed using the `getMediaType()` method. The supplied servlet application `SaxonServlet` uses this to set the media type in the HTTP header.

`normalization-form?`
: `"NFC" | "NFD" | "NFKC" | "NFKD" | "fully-normalized" | "none"` | _nmtoken_
: Indicates that a given Unicode normalization form (or no normalization) is required.

`omit-xml-declaration?`
: _boolean_
: For XML output this controls whether an XML declaration should be output; the default is `no`.

`parameter-document?`
: _uri_
: New in XSLT 3.0. Not implemented in Saxon 9.7. Allows serialization to be configured in an external document.

`standalone?`
: _boolean_ | `"omit"`
: Used only for XML output: if it is present, a standalone attribute is included in the XML declaration, with the value `yes` or `no`.

`suppress-indentation?`
: _eqnames_
: New in XSLT 3.0 (it was previously available in Saxon as an extension). The value is a whitespace-separated list of element names, and it typically identifies "inline" elements that should not cause indentation; in XHTML, for example, these would be `b`, `i`, `span`, and the like.

`undeclare-prefixes?`
: _boolean_
: Indicates XML 1.1 namespace undeclarations are to be output when required.

`use-character-maps?`
: _eqnames_
: A space-separated list of the names of character maps (see [`xsl:character-map`](xsl-character-map.md)) which will be applied to transform individual characters during serialization.

`version?`
: _nmtoken_
: Determines the version of XML or HTML to be output. This is largely documentary. However, for XML the distinction between 1.0 and 1.1 determines whether or not namespace undeclarations will be output; and for HTML, the value 5 can be used to force the HTML5 style of DOCTYPE declaration.

## Notes on the Saxon implementation

The new XSLT 3.0 attribute `parameter-document` is first implemented in Saxon 9.8.

## Details

The `xsl:output` declaration is always a top-level element immediately below the [`xsl:stylesheet`](xsl-stylesheet.md) element. There may be multiple `xsl:output` elements; their values are accumulated as described in the XSLT specification.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-output)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-output)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/output)

## See also

- [`xsl:character-map`](xsl-character-map.md)
- [`xsl:result-document`](xsl-result-document.md)
