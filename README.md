tory: Create Limited Role-Based Dashboards for Non-Issue Exceptions

Story Title: Implement Simplified NIE Dashboards with Role-Based Views (Status & Root Cause)

As a: NIE Issue Owner, NIE Issue Coordinator, or Administrator

I want: To view simple, relevant dashboard widgets summarizing Non-Issue Exceptions (NIEs) by Status and by Root Cause, filtered according to my role.

So that: I can get a quick overview of the NIEs I am responsible for or manage, using standardized data, and the old dashboards can be replaced.

Description:
This story involves replacing the existing dashboards related to Non-Issue Exceptions (NIEs) with a new, simplified dashboard experience. The new dashboard(s) will provide limited views focused primarily on summarizing NIEs based on their current status and their assigned (EIM-aligned Level 2) Root Cause.

Crucially, the data displayed will be restricted based on the logged-in user's role:

Administrators: Will see data aggregated across all NIEs.
Issue Owners: Will see data aggregated only for the NIEs where they are assigned as the owner.
Issue Coordinators: Will see data aggregated only for the NIEs where they are assigned as the coordinator.
(Assumption: If a user holds multiple roles, like Owner and Coordinator, they will see an aggregated view of all NIEs matching either criterion. This should be confirmed.)

Acceptance Criteria:

A new dashboard page/section dedicated to Non-Issue Exceptions is created and accessible.
A dashboard widget (e.g., bar chart, pie chart, table) exists that displays the count of NIEs grouped by their current Status.
A dashboard widget (e.g., bar chart, table) exists that displays the count of NIEs grouped by their assigned Level 2 EIM Root Cause (using the field implemented in the previous root cause story).
When logged in as a user with Administrator privileges, both the Status and Root Cause widgets reflect data aggregated from all NIE records in the system.
When logged in as a user assigned only as an Issue Owner on one or more NIEs, both widgets reflect data aggregated only from those specific NIEs where they are the owner.
When logged in as a user assigned only as an Issue Coordinator on one or more NIEs, both widgets reflect data aggregated only from those specific NIEs where they are the coordinator.
(Confirm Requirement) When logged in as a user who is assigned as an Issue Owner on some NIEs and an Issue Coordinator on others, both widgets reflect data aggregated from the combined set of those NIEs (all owned + all coordinated, without double-counting if owner=coordinator on the same NIE).
The dashboard widgets correctly query and display data from the Non-Issue Exception module.
The dashboard provides a clear and understandable visual summary of the data.
The previous/existing dashboards specifically for Non-Issue Exceptions are removed or made inaccessible to these users.
(Decision Point) No additional dashboard widgets beyond Status, Root Cause (and potentially a simple total count card) are included in this iteration, fulfilling the "very limited" requirement unless explicitly decided otherwise.
