Technical Observation:
This was caused by a process change on December 12, 2024.
Previously, annual decisions only required 1LOD approval.
After December 12, 2024, 2LOD confirmation became required if the 1LOD decision was to not perform a new risk assessment.
The issue occurred because the flag to generate a new annual decision was incorrectly set to "yes" despite the status being marked as "complete."
This did not have a material impact since the annual decision is generated 46 days before it’s due, and the correct decision was completed on time.
Only a small subset of records was affected.
3. Resolution:
The issue was already addressed through an incident ticket by:
Removing the duplicated annual decision records.
Correcting the calculation from <= DATETIMEVALUE("12/12/2024") to < DATETIMEVALUE("12/13/2024").
4. Action Plan:
Perform Post-Incident Validation (PIV):

Confirm that the corrected calculation is working as intended.
Ensure no further duplicate annual decisions are generated.
Enhance System Logic:

Implement a validation check to prevent a second annual decision from being generated if the status is already marked as "complete."
Add logging to capture when a second decision is attempted to be generated for tracking and troubleshooting.
Strengthen Monitoring and Reporting:

Create a system report to monitor for duplicate annual decisions.
Set up automated alerts if a second decision is triggered under similar conditions.
Communicate Process Change:

Inform 1LOD and 2LOD stakeholders about the process change and the updated decision logic.
5. Impact and Mitigation:
System Impact: Minor system update to enhance validation and reporting.
User Impact: No significant change in user process, as decisions are already handled within the updated workflow.
