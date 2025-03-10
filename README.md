Story Title: Migrate "Issues and Findings" to "Enterprise Issue Management" (EIM) and Create "Non-Issue Exceptions" Module

Story Type: Feature/Migration

Priority: High (Due to the scope and impact on issue management)

Assignee: (Assign to the appropriate developer or team)

Labels: migration, issue-management, enterprise-issue-management, non-issue-exceptions, data-migration, ui-change, regcomp

Description:

Problem Statement:

The "Issues and Findings" module is being migrated to "Enterprise Issue Management" (EIM) for standard issues. However, "Non-Issue Exceptions" need to be retained within RegComp. This requires creating a dedicated "Non-Issue Exceptions" module by copying the existing "Issues and Findings" module and making significant modifications to remove issue-related fields and adjust the workflow.

Technical Solution:

Module Duplication and Renaming:
Duplicate the existing "Issues and Findings" module within RegComp.
Rename the duplicated module to "Non-Issue Exceptions".
Archive the original "Issues and Findings" module as read-only.
Field Removal:
Remove the following fields from the "Non-Issue Exceptions" module:
"Slipped Status"
"At Risk"
"Action Plans"
"Original Expected Completion Date (OECD)"
"Revised Expected Completion Date (RECD)"
"RECD" (History)
"Additional Deliverables"
"Issue Reopening"
"Count of Slipped"
"Is this a plan for plan issue"
"Plan for Plan Issue"
"Executing Issues"
"Is Internal Audit confirmation required to close this issue"
"Is Regulatory confirmation required to close this issue"
"Submit to Issue Owner"
"Submit Action Plans for Review"
"Issue Coordinator Action Plan Review"
"Action Plan Review Comments"
"Set to In Progress"
"Submit Issue for Closure"
"Reviewed by GG05 or Above"
"Name of GG05 Reviewer"
"GG05 Reviewer"
"Issue Coordinator Closure Review"
"Issue Coordinator Closure Comments"
"Internal Audit Review"
"Internal Auditor"
"Internal Audit Review Comments"
"Internal Audit Review Date"
"RCM Lead / CCO / RCM EC Lead Closure Review"
"RCM Lead / CCO / RCM EC Lead Closure Comments"
"Closure Confirmed by Regulator"
"Regulator Closure Comments"
"Post-Closure Attachments"
"Minor Regulatory Observation"
"Issue Management Option"
Field Renaming and Value Modifications:
Rename "Issue ID" to "Non-Issue Exception ID".
Rename "Themes" to "Regulatory Themes".
Modify "Issue Status" to a dropdown list with the following values: "Draft", "In Progress", "Closed", and "Cancelled".
Issue Rating Logic:
Retain the fields for financial, regulatory, and reputational/stakeholder impact to determine the indicative issue rating.
Implement a validation rule: If the final issue rating (agreed or overridden) is not "Non-Issue Exception", direct the user to create the issue in "Enterprise Issue Management" (EIM).
Related Module Display:
Display "Non-Issue Exceptions" in the following modules:
"Assessable Unit"
"Control Result for Assessable Unit"
"Exam"
"Segment"
"Line of Business"
"Regulatory Theme"
Display the following fields for "Non-Issue Exceptions" in these modules: "Non-Issue Exception ID", "Subject", "Issue Status".






Story 2: Migrate Existing "Non-Issue Exceptions" Data to the New Module

Story Title: Migrate Existing "Non-Issue Exceptions" Data to the New Module

Story Type: Data Migration

Priority: Medium (Dependent on data volume and complexity)

Assignee: (Assign to the appropriate developer or team)

Labels: data-migration, non-issue-exceptions, regcomp

Description:

Problem Statement:

Following the creation of the new "Non-Issue Exceptions" module, existing data from the original "Issues and Findings" module that pertains to "Non-Issue Exceptions" needs to be migrated to the new module. This ensures data continuity and avoids data loss.

Technical Solution:

Data Identification and Extraction:
Identify the criteria for determining which records in the original "Issues and Findings" module are "Non-Issue Exceptions."
Extract the relevant data from the original module based on these criteria.
Data Transformation:
Transform the extracted data to match the schema and field names of the new "Non-Issue Exceptions" module.
Handle any data type conversions or data cleaning required.
Data Loading:
Load the transformed data into the new "Non-Issue Exceptions" module.
Data Validation:
Perform data validation to ensure that the migrated data is accurate and complete.
Compare the migrated data with
