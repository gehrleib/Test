Problem Statement:
Currently, sub-assessments for an Assessable Unit—Local Regulatory Environment Questionnaire, Regulatory Theme Checklist, and Control Assessment—each exist on separate tabs. This creates a poor user experience because users must navigate between tabs to view details.

Additionally, when a user completes a sub-assessment and saves it, they are automatically returned to the Assessable Unit record. However, the Assessable Unit may not immediately reflect the updated sub-assessment data because the system does not automatically recalculate the parent record upon return.

The software only loads the HTML of the active tab, meaning the system cannot detect changes from other tabs to determine if a recalculation is needed. To resolve this, all sub-assessments must be consolidated onto a single tab to enable real-time updates.

Furthermore, the "Assigned Users" fields currently appear at the top of the record, requiring users to scroll past potentially tens of delegates before reaching assessment details. This hinders usability. Moving these fields to a separate "Roles & Responsibilities" tab will improve navigation and readability.

Acceptance Criteria:
Consolidate Sub-Assessments:

Move Local Regulatory Environment Questionnaire, Regulatory Theme Checklist, and Control Assessment into a single tab under the Assessable Unit.

Ensure each sub-assessment is clearly separated and easily accessible within the new layout.

Auto-Refresh Assessable Unit:

When returning to the Assessable Unit after completing a sub-assessment, trigger an automatic recalculation.

Ensure the Assessable Unit reflects the latest sub-assessment data without requiring manual intervention.

Improve Readability by Moving Assigned Users:

Relocate all "Assigned User" fields (e.g., Delegates, Owners, Reviewers) to a new tab titled "Roles & Responsibilities."

Ensure users can still easily manage assignments without interfering with assessment details
