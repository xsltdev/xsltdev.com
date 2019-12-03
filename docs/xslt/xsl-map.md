---
description: Used to construct a new map
---

# xsl:map

Used to construct a new map.

_Available in XSLT 3.0. From Saxon 9.8, available in all editions. Implemented in Saxon-PE and Saxon-EE since Saxon 9.6._

- **Category**: instruction
- **Content**: _sequence-constructor_
- **Permitted parent elements**: any XSLT element whose content model is _sequence-constructor_; any literal result element
- **Element has no attributes**

## Details

The sequence constructor must evaluate to a sequence of maps. These can be constructed using [`xsl:map-entry`](xsl-map-entry.md) elements.

## Examples

### Example 1

```xslt
<xsl:variable name="week" as="map(xs:string, xs:string)">
    <xsl:map>
        <xsl:map-entry key="'Mo'" select="'Monday'"/>
        <xsl:map-entry key="'Tu'" select="'Tuesday'"/>
        <xsl:map-entry key="'We'" select="'Wednesday'"/>
        <xsl:map-entry key="'Th'" select="'Thursday'"/>
        <xsl:map-entry key="'Fr'" select="'Friday'"/>
        <xsl:map-entry key="'Sa'" select="'Saturday'"/>
        <xsl:map-entry key="'Su'" select="'Sunday'"/>
    </xsl:map>
</xsl:variable>
```

### Example 2

```xslt
<xsl:variable name="index" as="map(xs:string, element(employee))">
    <xsl:map>
        <xsl:for-each select="//employee">
            <xsl:map-entry key="@empNr" select="."/>
        </xsl:for-each>
    </xsl:map>
</xsl:variable>
```

## Links

- [XSLT 3.0 Specification](http://www.w3.org/TR/xslt-30/#element-map)
- [Saxon](http://saxonica.com/documentation/index.html#!xsl-elements/map)

## See also

- [`xsl:map-entry`](xsl-map-entry.md)
