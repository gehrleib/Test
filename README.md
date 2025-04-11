Story Title: Refactor Control Assessment Generation to Set "Presence of Control Issues" Based on EIM Data

As a: System Administrator / Risk Manager

I want: The "Presence of Control Issues" field on a newly generated Control Assessment to be automatically set based on the status and rating of the associated issue ingested from the Enterprise Issue Management (EIM) system

So that: The initial assessment state accurately reflects high-priority open issues sourced from the authoritative EIM system, even though the data is read-only in our system.

Description:
Currently, when a Control Assessment is generated, the "Presence of Control Issues" field is set to "Yes" if the associated internal issue has a Final Issue Rating of "1" or "2" and is "Open".
We are migrating issue management to EIM and will be ingesting EIM issues as read-only data.
This story involves updating the assessment generation process to query the ingested EIM issue data instead of the old internal issue data to determine the initial value for the "Presence of Control Issues" field. The core logic remains the same: set to "Yes" if the linked EIM issue is "Open" and has a rating equivalent to "1" or "2". Otherwise, it should be set to "No" (or its default).

Acceptance Criteria:

Given a Control Assessment is being generated for a control linked to an ingested EIM issue; When the linked EIM issue has a status representing "Open" AND its rating/severity maps to the equivalent of "1" or "2"; Then the "Presence of Control Issues" field on the generated Control Assessment is automatically set to "Yes".
Given a Control Assessment is being generated for a control linked to an ingested EIM issue; When the linked EIM issue has a status not representing "Open" (e.g., "Closed", "Resolved") OR its rating/severity does not map to the equivalent of "1" or "2"; Then the "Presence of Control Issues" field on the generated Control Assessment is automatically set to "No" (or the system default).
Given a Control Assessment is generated for a control not linked to a relevant ingested EIM issue; Then the "Presence of Control Issues" field is set to "No" (or the system default).
After the Control Assessment is generated and the field is auto-populated, users must still have the ability to manually change the value of the "Presence of Control Issues" field.
The system correctly identifies and uses the appropriate fields from the read-only ingested EIM data structure for "Status" and "Rating/Severity".
The logic does not automatically update the "Presence of Control Issues" field from "Yes" to "No" if the linked EIM issue's status changes after the assessment has been generated (maintaining current behavior).
Notes/Assumptions:

Assumes the EIM issue ingestion process (your story #2) is complete or sufficiently defined to identify the relevant fields (Status, Rating/Severity) and the linkage between Controls/Assessments and EIM issues.
Requires clear mapping definition between EIM status/rating values and the concepts of "Open" and ratings "1"/"2".
The default value if conditions are not met is assumed to be "No", clarify if different.
