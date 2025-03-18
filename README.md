Technical Observation:
The blank value does not meet the conditions to be sent to CALMA, which is expected since overridden controls are intended to be out of scope.
This is a cosmetic issue that did not affect the system's functionality or the accuracy of M&T activities.
3. Solution:
Convert the "Next Control Test Year (Final)" field from a value list to a numeric field to allow any numeric value beyond 2030.
Update all layouts, reports, and notifications to reflect the new numeric field.
Inform users who rely on this field in their API integrations to update their configurations accordingly.
Conduct system testing to ensure the new field functions as expected and does not disrupt existing processes.
4. Impact and Mitigation:
System Impact: Minor impact on system functionality and reporting due to field conversion.
User Impact: Potential impact on users with API integrations using the old field.
Mitigation: Provide clear communication and documentation to affected users.
Operational Impact: No direct impact on M&T activities since these controls are already treated as out of scope.
