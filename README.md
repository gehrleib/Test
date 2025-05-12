<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0"
    xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

  <xsl:output method="xml" indent="yes"/>

  <!-- Match root and copy -->
  <xsl:template match="/Findings">
    <Findings>
      <!-- Apply template to only Finding elements with Yes -->
      <xsl:apply-templates select="Finding[Non_Issue_Identifier='Yes']"/>
    </Findings>
  </xsl:template>

  <!-- Copy the matching Finding as-is -->
  <xsl:template match="Finding">
    <xsl:copy>
      <xsl:apply-templates select="@* | node()"/>
    </xsl:copy>
  </xsl:template>

  <!-- Copy attributes and child nodes -->
  <xsl:template match="@* | node()">
    <xsl:copy>
      <xsl:apply-templates select="@* | node()"/>
    </xsl:copy>
  </xsl:template>

</xsl:stylesheet>
