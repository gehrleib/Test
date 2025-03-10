Got it, let's craft a Jira story that addresses the automatic delinking of assessable units and controls when segment scopes change.

Story Title: Automatically Delink Assessable Units and Controls on Segment Scope Change (Draft Plans)

Story Type: Feature/Improvement

Priority: High (Adjust based on the potential risk of incorrect scope)

Assignee: (Assign to the appropriate developer or team)

Labels: automation, data-integrity, assessable-units, monitoring-testing, segment-change, draft-plans, addendum

Description:

Problem Statement:

Currently, the system automatically links assessable units to "master" monitoring & testing plans based on segment scope. However, when a segment's scope changes (e.g., "Personal & Commercial Banking" to "Personal Banking"), the system fails to automatically remove assessable units and controls that are no longer within the updated scope. This leads to inaccurate plan data, potential compliance issues, and increased manual effort to correct the discrepancies. This problem impacts both standard "master" plans and "addendum" type plans, but the addendum plans need to have the controls delinked, not the assessable units. This problem only occurs when the plans are in a "Draft" status.

Technical Solution:

Segment Scope Change Detection:
Implement a mechanism to detect changes in segment scope. This could involve triggering a process when a segment's definition is updated.
Assessable Unit/Control Scope Validation (Draft Plans):
When a segment scope change is detected, and affected monitoring & testing plans are in "Draft" status:
For "Master" Plans:
Identify assessable units linked to the plan that are no longer within the updated segment scope.
Automatically delink these assessable units from the "master" plan.
For "Addendum" Plans:
Identify controls linked to the plan that are no longer within the updated segment scope.
Automatically delink these controls from the "addendum" plan.
