<xsl:stylesheet version="3.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
  <xsl:output method="xml" indent="yes"/>

  <xsl:template match="/Records">
    <RegionalSegments>
      <xsl:for-each-group select="Record" group-by="Field[@id='21279']/ListValues/ListValue">
        <xsl:for-each-group select="current-group()" group-by="Field[@id='21256']/Reference/@id">
          <RegionalSegment>
            <Region>
              <xsl:value-of select="Field[@id='21279']/ListValues/ListValue"/>
            </Region>
            <Segment_ID>
              <xsl:value-of select="Field[@id='21256']/Reference/@id"/>
            </Segment_ID>
            <Regional_Segment>
              <xsl:value-of select="concat(Field[@id='21256']/Reference, ' - ', Field[@id='21279']/ListValues/ListValue)"/>
            </Regional_Segment>
          </RegionalSegment>
        </xsl:for-each-group>
      </xsl:for-each-group>
    </RegionalSegments>
  </xsl:template>
</xsl:stylesheet>
