Technical Observation:
There is a technical limitation that prevents mandatory fields from being enforced when values are edited directly on a report (inline edit).
This was a design decision to avoid increased complexity and system load times, as requiring users to navigate to individual records would slow down processes.
The total number of controls in scope for M&T is approximately 40,000.
3. Solution:
Disable the inline edit functionality to ensure commentary is provided when an override is applied.
Require users to navigate to the individual record to input an override and its corresponding commentary.
Maintain the same user permissions—users who could previously perform inline edits will retain the ability to update the record directly.
Commentary can still be added at any time but will be enforced when an override is present.
4. Impact and Mitigation:
User Impact: Increased time required to update records due to the removal of inline editing.
Mitigation: Communicate the change and provide guidance on efficient record updates.
Operational Impact: Ensures all overrides have appropriate documentation, improving auditability and compliance.
System Impact: No major system changes other than disabling inline editing.
