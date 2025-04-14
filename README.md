As an Exam Reviewer/User,
I want the Exam record functionality within RegComp to be updated,
So that it accurately displays linked issues ingested from Enterprise Issue Management (EIM), uses the severity from these EIM issues to determine the Final Exam Rating, and aligns with the new workflow where issues must originate in EIM.

Background:
Previously, Exam records were linked to native Issues created directly within RegComp, and users could create these issues from an Exam. The Issue Severity from these native RegComp issues influenced the Final Exam Rating. Now, issue creation is centralized in Enterprise Issue Management (EIM). EIM issues are ingested into RegComp as read-only records. This story focuses on updating the Exam record to work with these ingested EIM issues, removing the old functionality.

Acceptance Criteria:

Exam records can be associated/linked with the relevant read-only EIM Issue records that have been ingested into RegComp.
When viewing an Exam record, a section clearly displays all associated EIM Issues.
The displayed list/section of associated EIM issues must show the following information for each linked issue:
EIM Issue ID (or RegComp's identifier for the ingested EIM issue)
Subject
Description
Severity
Expected Completion Date
Status
The data displayed for the linked EIM issues must originate solely from the read-only records ingested from EIM into RegComp.
The business logic for calculating the "Final Exam Rating" for an Exam record must be modified to use the "Severity" value(s) from the linked EIM Issues, replacing the previous reliance on native RegComp issue severity. (Note: Define aggregation logic if multiple issues - e.g., highest severity).
All UI elements (buttons, links, menu options) that previously allowed users to create a new native Issue directly from the Exam record interface must be removed or disabled.
Users attempting any action that would have previously created a native issue from the Exam should be guided towards creating the issue in EIM instead (e.g., via informational text or a disabled control tooltip, if appropriate).
The display of EIM issue details within the Exam record interface must be read-only, reflecting the nature of the ingested data.
