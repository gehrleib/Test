<xsl:stylesheet version="3.0"
  xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
  exclude-result-prefixes="#all">

  <xsl:output method="xml" indent="yes"/>

  <xsl:template match="/Records">
    <ArcherRecords>
      <xsl:for-each select="Record/Record[@levelGuid='b93fb323-e99a-4fd6-964d-45b33f7a8f9a']">
        <xsl:variable name="level2" select="."/>
        <xsl:variable name="level1" select=".."/>
        <xsl:variable name="level0" select="$level1/Field[@guid='ee0594ca-26fc-4304-9137-c5834e150f27']/ListValues/ListValue"/>

        <ArcherRecord>
          <!-- Level 2 -->
          <Level2ID><xsl:value-of select="$level2/@contentId"/></Level2ID>
          <Level2Name><xsl:value-of select="$level2/Field[@guid='b8987522-57c7-41ed-875f-5f55960cd95c']"/></Level2Name>
          <xsl:if test="normalize-space($level2/Field[@guid='35dd43ab-bbdb-478a-9026-4dc023ba6088'])">
            <Level2Description>
              <xsl:value-of select="$level2/Field[@guid='35dd43ab-bbdb-478a-9026-4dc023ba6088']"/>
            </Level2Description>
          </xsl:if>
          <xsl:if test="$level2/Field[@guid='8c3a3efb-7bbd-4a7e-a4ac-5c18dbf6711d']/ListValues/ListValue/@displayName">
            <Type>
              <xsl:value-of select="$level2/Field[@guid='8c3a3efb-7bbd-4a7e-a4ac-5c18dbf6711d']/ListValues/ListValue/@displayName"/>
            </Type>
          </xsl:if>
          <Status>Active</Status>

          <!-- Level 1 -->
          <Level1ID><xsl:value-of select="$level1/@contentId"/></Level1ID>
          <Level1Name><xsl:value-of select="$level1/Field[@guid='97f24cb9-f9fa-4f15-8834-9788c88efb8d']"/></Level1Name>
          <xsl:if test="normalize-space($level1/Field[@guid='27e3cad8-bb98-49ea-b019-7fa006b89570'])">
            <Level1Description>
              <xsl:value-of select="$level1/Field[@guid='27e3cad8-bb98-49ea-b019-7fa006b89570']"/>
            </Level1Description>
          </xsl:if>

          <!-- Level 0 -->
          <xsl:if test="$level0">
            <Level0ID><xsl:value-of select="$level0/@id"/></Level0ID>
            <Level0Name><xsl:value-of select="$level0/@displayName"/></Level0Name>
          </xsl:if>
        </ArcherRecord>
      </xsl:for-each>
    </ArcherRecords>
  </xsl:template>

</xsl:stylesheet>
