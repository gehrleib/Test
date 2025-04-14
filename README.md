I want the existing integration between CALMA and RegComp to be refactored,
So that only records identified as "Non-Issue Exceptions" are ingested and logged into RegComp, ensuring accurate record-keeping and separation from regular issues now managed by Enterprise Issue Management (EIM).

Background:
Currently, the integration ingests both Issues and Non-Issue Exceptions from CALMA files into RegComp. A separate initiative (covered in another story/epic: [Link to EIM Story/Epic if available]) is redirecting the handling of regular Issues to the Enterprise Issue Management (EIM) system. This story focuses only on modifying the existing integration path to RegComp to handle the remaining Non-Issue Exceptions, which serve a logging purpose within RegComp.

Acceptance Criteria:

Given the integration process runs, When it processes files provided by CALMA, Then it must filter records based on the "Non Issue Identifier" field.
Given a record in the CALMA file has "Non Issue Identifier" = "Yes", When the integration processes this record, Then the record must be ingested into the RegComp system.
Given a record in the CALMA file does not have "Non Issue Identifier" = "Yes" (e.g., it's "No", blank, or null), When the integration encounters this record, Then it must be ignored/skipped by this process and not sent to RegComp.
Given a Non-Issue Exception record is successfully ingested into RegComp, Then it must contain the following fields populated from the CALMA source:
Subject
Description
Root Cause
Source
Relation Control
Assessable Unit
Given a Non-Issue Exception record is successfully ingested into RegComp, Then the corresponding record/item within RegComp must be automatically marked as "Closed" (or equivalent terminal status).
Given the refactored integration is running, Then no records identified as regular Issues (i.e., not Non-Issue Exceptions) should be processed or sent to RegComp via this integration path.
Given the integration process runs, Then appropriate logging must be in place to monitor the filtering, ingestion, and auto-closure steps, including handling any errors.
Technical Notes/Considerations:

The source data is from existing files provided by CALMA. Confirm file format and location remain unchanged.
The key filtering field is "Non Issue Identifier". Confirm the exact value representing a non-issue exception is "Yes".
The target system for these records is RegComp.
The primary function in RegComp is logging; limited fields are required.
Auto-closure mechanism within RegComp needs to be triggered post-ingestion.
This refactoring should consider potential impacts on existing error handling and monitoring for the integration.
Coordinate with the team working on the EIM integration to ensure no overlap or data loss during transition.
