Problem Statement:

Currently, users create regulations by manually selecting a combination of Segment, Line of Business, Country, and Theme. This regulation is then linked to a control. This process is prone to human error, leading to the creation of "orphaned" controls where the regulation combination does not accurately match any existing Assessable Unit. This results in compliance gaps, inaccurate reporting, and increased manual review efforts to identify and rectify these discrepancies.

As a user responsible for creating and maintaining controls,
I want to directly link controls to Assessable Units,
so that I can ensure the control is accurately associated with a valid Assessable Unit, eliminating the risk of orphaned controls.

Technical Solution:

Remove Regulation as an intermediary: Eliminate the need to create a separate Regulation entity.
Direct Association: Implement a direct association between Controls and Assessable Units.
Assessable Unit Selection: When creating or editing a Control, provide a dropdown or searchable list of existing Assessable Units.
Validation: Implement validation to ensure that a Control is always linked to a valid Assessable Unit.
Assessable Unit Status Display: Display the status of the selected Assessable Unit (e.g., Draft, 2LOD Review, Approved, Retired) within the Control creation/edit interface.
Data Migration: Develop a migration script to:
Identify existing controls linked to regulations.
Map the regulation attributes (Segment, Line of Business, Country, Theme) to existing Assessable Units.
Directly link the controls to the corresponding Assessable Units.
Flag any controls that cannot be automatically mapped for manual review.
UI/UX Improvements: Enhance the user interface to clearly display the linked Assessable Unit and its status on the Control details page.
Audit Trail: Maintain an audit trail of all changes made to Control-Assessable Unit associations.
Reporting: Modify existing reports to reflect the direct Control-Assessable Unit relationship.