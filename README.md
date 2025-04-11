Story: Refactor Risk Assessment Trigger Logic to Use EIM Issue Data

Story Title: Adapt Automated Risk Assessment Triggers to Use EIM Issue Data Source

As a: Risk Management System / Process Owner

I want: The automated process that triggers new Risk Assessments for Assessable Units to use the ingested EIM issue data (status, severity, dates, linkage) instead of the legacy internal issue data.

So that: Risk Assessments are initiated based on the authoritative EIM data for high-severity issue events (progression and closure), ensuring timely risk reviews aligned with enterprise issue management.

Description:
We have an existing automated process that forces the creation of a new Risk Assessment for an Assessable Unit based on two conditions related to linked issues:

Issue In Progress: When a linked issue (Severity "1" or "2") moves to an "In Progress" state, and its "In Progress Date" is later than the Assessable Unit's "Last Approved Date".
All High-Severity Issues Closed: When the last remaining linked issue with Severity "1" or "2" for an Assessable Unit is moved to a "Closed" state.
This story requires refactoring this automation to query the read-only ingested EIM issue data for all necessary issue information (status, severity mapping, relevant dates, linkage to Assessable Units) instead of using the current internal issue source. The core triggering logic/conditions remain the same, but the data source changes.

Acceptance Criteria:

Trigger 1: Issue Progress (Based on EIM Data)

Given an Assessable Unit X with a "Last Approved Date". When an EIM issue linked to Assessable Unit X is updated, reflecting a transition to an "In Progress" status (based on EIM status codes/logic) AND the EIM issue's severity maps to "1" or "2" AND the relevant date associated with the EIM issue becoming "In Progress" is later than the Assessable Unit X's "Last Approved Date". Then a new Risk Assessment is triggered for Assessable Unit X.
Given the same scenario as above, but the EIM issue's "In Progress" date is not later than the Assessable Unit X's "Last Approved Date" OR the EIM issue severity does not map to "1" or "2". Then a new Risk Assessment is not triggered by this specific event.
Trigger 2: All High-Severity Issues Closed (Based on EIM Data)
3.  Given an Assessable Unit X.
When an EIM issue linked to Assessable Unit X is updated, reflecting a transition to a "Closed" status (based on EIM status codes/logic) AND that EIM issue's severity mapped to "1" or "2" AND no other EIM issues linked to Assessable Unit X remain in an "Open" state (based on EIM status) with severity mapping to "1" or "2".
Then a new Risk Assessment is triggered for Assessable Unit X.
4.  Given the same scenario as above, but other EIM issues linked to Assessable Unit X still remain in an "Open" state with severity mapping to "1" or "2".
Then a new Risk Assessment is not triggered by this specific closure event.

General Criteria:
5.  The automated process correctly queries the ingested EIM data source.
6.  The process correctly interprets EIM fields/values corresponding to: Issue Status ("Open", "In Progress", "Closed"), Issue Severity ("1", "2"), relevant dates ("In Progress Date", "Closed Date" - or equivalents), and the linkage between EIM Issues and internal Assessable Units.
7.  The process functions correctly using the read-only EIM data.
8.  Appropriate logging is in place to track trigger events and data used.
