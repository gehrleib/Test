<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="3.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <xsl:output method="xml" indent="yes"/>
    
    <!-- Define current year -->
    <xsl:variable name="currentYear" select="format-date(current-date(), '[Y]')"/>
    
    <xsl:template match="/Records">
        <ArcherRecords>
            <!-- Select records where the Plan Year does not match the current year -->
            <xsl:for-each select="Record[@levelGuid='877e196d-27cd-488f-9c33-3ea0cd2a8561']
                [Field[@guid='7b8fb31d-eb30-4216-acab-fd0658d4cf12'] != $currentYear]">
                
                <ArcherRecord>
                    <Plan_ID>
                        <xsl:value-of select="Field[@guid='5fd374e6-81bc-47be-924a-b7c1f1892fed']"/>
                    </Plan_ID>
                </ArcherRecord>
            </xsl:for-each>
        </ArcherRecords>
    </xsl:template>
</xsl:stylesheet>
