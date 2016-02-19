---
title: Font configuration in PDF2
layout: post
tags: dita-ot pdf2
---
**TL;DR**: You might be doing it wrong.

## Background

Back when PDF2 was originally developed, FOP didn't support the font-selection-strategy property. This mean it was impossible to change the font per character if the font that was used didn't contain a particular glyph. An FO preprocessing step called _I18N_ was added to DITA-OT to enable per character font selection. FOP still doesn't support per-character font selection, so if FOP is used the I18N processing may still be needed when the fonts don't contain all glyphs needed.

## What is I18N processing

While I18N is a numeronym for internationalization, the I18N processing in PDF2 really has nothing to do with internationalization. Instead, it's a font mapping process that takes the content language into consideration:

1.  When DITA is converted to FO with XSLT, the font-family property uses a logical font name. The logical font-family name can be anything, but the default values are e.g. Serif, Helvetica, or Monospaced. It is only a name and doesn't need to match to the actual fonts that will be used. The output from this stage is e.g.
    
    ```xml
    <fo:block font-family="Serif">Copyright © 1999.</fo:block>
    ```
1.  All text content in the generated FO file is processed to categorize every character into a character group. These groups include SymbolsSuperscript, Symbols, or Japanese. To which group a given character will belong to is configured in language specific configuration files. If no special group is configured for a character, it's considered to be part of the special "default" group. Consecutive characters belonging to the same group are collapsed into a single sequence. Output for this process is e.g.:
    
    ```xml
    <fo:block font-family="Serif">
      Copyright <opentopic-i18n:text-fragment char-set="SymbolsSuperscript"
        >©</opentopic-i18n:text-fragment> 1999.
    </fo:block>
    ```
1.  Then the FO file is processed again to resolve the font for each group. The logical font family is read from the closest ancestor FO element. Then the font mapping configuration is used to look up the physical font for each combination of logical font and character group. The font mapping can also change the character's base-line and size. Output from this is e.g.
    
    ```xml
    <fo:block font-family="Times New Roman, Times">
      Copyright <fo:inline font-family="Times New Roman, Times"
        baseline-shift="20%" font-size="smaller">©</fo:inline> 1999.
    </fo:block>
    ```

Font mapping thus allows changing fonts per language, e.g. using Helvetica for English and AdobeMyungjoStd-Medium for Korean, or making a given character superscript without marking up the character in DITA source with <sup>.

However, if you actually want to do this, you need to configure the character groups for each language and also create a group for each language. Without the group configuration, you can't e.g. use a separate fonts for Japanese and Swedish.

The 18N font mapping is complex, difficult to extend, and lengthens processing time. For some complex cases it is suitable, but for the majority of cases a more simple approach is preferred.

## The right way

When font mapping process is not needed, it can be simply disabled by setting property `org.dita.pdf2.i18n.enabled` to `false`. Then the stylesheet that convert DITA to FO need to be updated to use physical font-families instead of the logical font families. For example the following attribute-sets that use logical font families

```xml
<xsl:attribute-set name="__fo__root">
  <xsl:attribute name="font-family">serif</xsl:attribute>
</xsl:attribute-set>
<xsl:attribute-set name="common.title">
  <xsl:attribute name="font-family">sans-serif</xsl:attribute>
</xsl:attribute-set>
```

can be changed to

```xml
<xsl:attribute-set name="__fo__root">
  <xsl:attribute name="font-family">Times New Roman, Times</xsl:attribute>
</xsl:attribute-set>
<xsl:attribute-set name="common.title">
  <xsl:attribute name="font-family">Helvetica, Arial Unicode MS</xsl:attribute>
</xsl:attribute-set>
```

That's it, all your fonts are configured. If you need to e.g. change the font per language, you can use e.g.

```xml
<xsl:attribute-set name="__fo__root">
  <xsl:attribute name="font-family">
    <xsl:choose>
      <xsl:when test="$locale.lang = 'jp'">KozMinProVI-Regular</xsl:when>
      <xsl:otherwise>Times New Roman, Times</xsl:otherwise>
    </xsl:choose>
  </xsl:attribute>
</xsl:attribute-set>
```

## Conclusion

The font mapping process has its use cases and it's a working solution. However, if your font configuration needs are simple and you're still using font mapping process, you're doing it wrong. The default in PDF2 is to use I18N processing because of backwards compatibility, but this is something that will probably change in DITA-OT 3.0. The font mapping process code will still be available, but will not be enabled by default. The DITA-OT PDF plugin generator already generates code where font mapping process is disabled. Thus, if you're able to move over to the simple font configuration model, there's not reason to delay.
