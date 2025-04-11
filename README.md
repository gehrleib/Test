<xsl:stylesheet version="3.0"
                xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
                xmlns:xs="http://www.w3.org/2001/XMLSchema"
                exclude-result-prefixes="xs">

  <xsl:output method="xml" indent="yes" encoding="UTF-8"/>
  <xsl:strip-space elements="*"/> <xsl:variable name="guid1" select="'16abaf8f-01e5-49cc-b8d1-e2bd6d0d5c91'" static="yes"/>
  <xsl:variable name="guid2" select="'c16c458c-c577-4c63-af63-b96f2b35ef20'" static="yes"/>

  <xsl:template match="/Records">
    <ArcherRecords>
      <xsl:apply-templates select="Record[(Field[@guid=$guid1] &lt;= Field[@guid=$guid2]) or not(string(Field[@guid=$guid2]))]"/>
    </ArcherRecords>
  </xsl:template>

  <xsl:template match="Record">
    <ArcherRecord>
      <CRAUID>
        <xsl:value-of select="@contentId"/>
      </CRAUID>
    </ArcherRecord>
  </xsl:template>

</xsl:stylesheet>
