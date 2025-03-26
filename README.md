Background
The Global Value List "RCM - Theme Type" is used across the Regulatory Compliance Management (RCM) program to categorize Regulatory Themes. We need to rename the existing value "Reliance Model" to "FCOP" to reflect updated terminology.

This change ensures that all references to "Reliance Model" across the application are seamlessly updated to "FCOP", with no additional modifications required in downstream systems or workflows.

Implementation Steps
Update the Global Value List

Locate the "RCM - Theme Type" Global Value List in Archer.

Rename the value "Reliance Model" to "FCOP".

Save and apply the change.

Verify the Impact Across the System

Since this is a Global Value List update, the change will automatically reflect across all records, reports, and references where the value is used.

No database updates or reprocessing of existing records are required.

Testing Approach
Navigate to a Regulatory Theme record.

Locate the Theme Type field.

Confirm that the value "Reliance Model" has been successfully renamed to "FCOP".

Verify that historical records and reports now display "FCOP" instead of "Reliance Model".

Assumptions & Considerations
No integrations or downstream dependencies require updates since this is a simple value rename within the Archer platform.
