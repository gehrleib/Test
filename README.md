<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="3.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <xsl:output method="xml" indent="yes"/>

    <!-- Define current year -->
    <xsl:variable name="currentYear" select="format-date(current-date(), '[Y]')"/>

    <xsl:template match="/Records">
        <ArcherRecords>
            <!-- Process each regional segment -->
            <xsl:for-each select="Record">
                <xsl:variable name="regionalSegmentID" select="Field[@guid='5e12c2fb-f926-4a1a-8ddf-fbb01392d1a5']"/>

                <!-- Find existing master plan for the current year -->
                <xsl:variable name="existingMasterPlan" select="
                    Record[@levelGuid='877e196d-27cd-488f-9c33-3ea0cd2a8561']
                    [Field[@guid='2db64bce-7cc9-42c2-8685-a81943e9c7ec']/ListValues/ListValue[@displayName='Master']]
                    [Field[@guid='7b8fb31d-eb30-4216-acab-fd0658d4cf12'] = $currentYear]
                "/>

                <!-- If no plan exists or if it's canceled, create a new record -->
                <xsl:if test="not($existingMasterPlan) or $existingMasterPlan/Field[@guid='8fe9b331-20fe-4642-864d-12ce1a384638']/ListValues/ListValue[@displayName='Canceled']">
                    <ArcherRecord>
                        <RegionalSegmentID>
                            <xsl:value-of select="$regionalSegmentID"/>
                        </RegionalSegmentID>
                        <Plan_Type>Master</Plan_Type>
                        <Plan_Year>
                            <xsl:value-of select="$currentYear"/>
                        </Plan_Year>
                    </ArcherRecord>
                </xsl:if>
            </xsl:for-each>
        </ArcherRecords>
    </xsl:template>
</xsl:stylesheet>
