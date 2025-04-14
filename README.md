Acceptance Criteria:

The integration must read and process the existing files provided by CALMA.
The integration must filter records based on the value in the "Non Issue Identifier" field.
Only records with "Non Issue Identifier" = "Yes" will be selected for processing into RegComp.
Records where "Non Issue Identifier" is not equal to "Yes" (or is blank/null) must be skipped by this integration path and not sent to RegComp.
Selected Non-Issue Exception records must be successfully ingested into the RegComp system.
The ingested records in RegComp must accurately contain the following fields mapped from the CALMA source file:
Subject
Description
Root Cause
Source
Relation Control
Assessable Unit
Upon successful ingestion into RegComp, the corresponding Non-Issue Exception record must be automatically updated to a "Closed" (or equivalent terminal) status within RegComp.
No records identified as regular Issues (i.e., those not meeting the "Non Issue Identifier" = "Yes" criteria) should reach RegComp through this refactored integration.
The integration process must include sufficient logging to verify successful processing (filtering, ingestion, auto-closure) and to diagnose any errors.
