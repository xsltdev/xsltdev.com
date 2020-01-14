---
description: Causes a message to be displayed
---

# xsl:message

Causes a message to be displayed.

_Available in XSLT 1.0 and later versions. Available in all Saxon editions._

- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element

## Attributes

`select?`

_expression_

The content of the message may be specified using either or both of the `select` attribute and the enclosed sequence constructor. If a `select` attribute is used, then the value must be an XPath expression, and the effect is the same as if a single [`xsl:copy-of`](xsl-copy-of.md) element with this `select` attribute were added to the start of the sequence constructor.

`terminate?`

_{ boolean }_

If the value is set to `yes`, processing of the stylesheet is terminated after issuing the message. The default is `no`. This attribute may be supplied as an attribute value template.

`error-code?`

_{ eqname }_

New in XSLT 3.0. Specifies the error code associated with the message. The effective value should be an EQName. The default is `Q{http://www.w3.org/2005/xqt-errors}XTMM9000`.

`saxon:time?`

_boolean_

If the value is set to yes, a timestamp is added at the start of the message. The default is `no`. Requires Saxon-PE or Saxon-EE.

## Notes on the Saxon implementation

The Saxon optimizer attempts to ensure, as far as possible, that calls to `xsl:message` behave in a predictable way: for example a call on `xsl:message` within a loop will not be lifted out of the loop. However, this doesn't work at a distance: if a function calls `xsl:message` and the function is called within a predicate, it is unpredictable how often the function will be called, and therefore how many messages will be produced.

From Saxon 9.5 the new feature of text value templates is implemented, which is particularly useful with `xsl:message`. For example:

```xslt
<xsl:message expand-text="yes">Id: {@id} Age: {@age} Status: {@status}</xsl:message>
```

The attribute `expand-text="yes"` can appear on any ancestor element to enable the feature.

Saxon 9.8 includes a new extension function `saxon:message-count()` which can be used to count the number of messages that have been issued, either overall or with a specific error code. This can be used, for example, to terminate execution after a certain number of warning conditions have occurred.

## Details

By default the message is displayed on the standard error output stream. You can supply your own message receiver if you want it handled differently. This must be a class that implements the `Receiver` interface. The content of the message is in general an XML fragment. You can supply the `Receiver` using the `-m` option on the command line, or the `setMessageEmitter()` method of the `Controller` class.

The sequence of calls to this `Receiver` is as follows: there is a single `open()` call at the start of the transformation, and a single `close()` call at the end; and each evaluation of an `xsl:message` instruction starts with a `startDocument()` call and ends with `endDocument()`. The `startDocument()` event has a `properties` argument indicating whether `terminate="yes"` was specified, and the `locationId` on calls such as `startElement()` and `characters()` can be used to identify the location in the stylesheet where the message data originated (this is achieved by passing the supplied `locationId` in a call to `getPipelineConfiguration().getLocator().getSystemId(locationId)`, or to `getLineNumber()` on the same object).

From Saxon 9.8, if the `xsl:message` instruction defines an error code, this code will be notified to the `Receiver` by means of a processing instruction event. The name of the processing-instruction is `error-code`; the string value is the error code as an `EQName`. The `processingInstruction()` event occurs immediately after the `startDocument()` event.

Select the class `MessageWarner` to have `xsl:message` output notified to the JAXP `ErrorListener`, as described in the JAXP documentation.

## Links

- [XSLT 2.0 Specification](http://www.w3.org/TR/xslt20/#element-message)
- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-message)
- [Saxon](https://www.saxonica.com/html/documentation/xsl-elements/message.html)

## See also

- [`xsl:result-document`](xsl-result-document.md)
