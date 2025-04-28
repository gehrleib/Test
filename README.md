RegComp System Enhancements – Summary
1. Unified Regulatory Content Overview Dashboard
Previous State:

Separate dashboards existed:

A mapping dashboard for Canada.

A mapping dashboard for all other jurisdictions.

An impact assessment dashboard for Regulatory Content Leads.

Current Enhancement:

A single dashboard called Regulatory Content Overview has been created.

The dashboard dynamically adjusts based on a user's assigned role.

Users with multiple roles can now view all their tasks in a single consolidated view.

2. Unified Mapping Process for Other Jurisdictions
Previous State:

For Canada, mapping was already done at the Assessable Unit level.

For Other Jurisdictions, mapping was done differently:

Users selected the Impacted Lines of Business (LoBs) instead of the Assessable Units directly.

The system would then infer which Assessable Units were impacted based on those LoBs.

Issues with Previous Approach for Other Jurisdictions:

Indirect assignment:
Mapping via LoBs did not allow users to select Assessable Units directly, making it difficult to later assign regulatory groups explicitly.

Post-mapping challenges:
Once a regulation completed the mapping step, it was difficult to retroactively assign it to individual Assessable Units without system workarounds.

Risk of incomplete jurisdictional mapping:
If a Regulatory Group impacted multiple jurisdictions, it only required one user to complete the mapping.

This meant users in other jurisdictions might never get the opportunity to map their relevant Assessable Units.

Increased risk of missing assignments:
This approach increased the likelihood that an Assessable Unit would remain unassigned to any regulation or regulatory group.

Current Enhancement:

All jurisdictions (including Other Jurisdictions) now map at the Regulatory Group level.

Users now select the relevant Assessable Units directly when completing their mapping tasks.

Additionally, for Regulatory Groups impacting multiple regions:

A separate attestation record is created for each impacted regional segment.

Regional segments are determined based on:

The segment associated with the Regulator/Issuing Body.

The jurisdiction/country of the regulation or issuance.

This ensures each jurisdiction maps their own Assessable Units independently and no jurisdiction is unintentionally skipped.

3. Role-Based Action Permissions
Action Permissions:

Only users assigned one of the following roles at a regional segment level can perform actions:

Regulatory Content Validator

Regulatory Content Mapper

Regulatory Content Lead (Impact Assessment)

Impact of Enhancement:

Users can only act within their assigned regional segment (e.g., a user in Capital Markets – Canada cannot act on Capital Markets – United States tasks).

The Regulatory Content Overview dashboard displays only records impacting the user's assigned regional segments and roles.

4. Introduction of Two New Processes
1. Validation Forms:

Allows Validators to scope or descope Regulatory Groups.

For example: Confirm if a group applies to RBC or imposes requirements.

Decisions are formally logged within RegComp.

2. Change Requests:

Enables users to propose changes to Regulatory Group structures.

Types of Change Requests:

Adjust regulatory group coverage (e.g., from Sections 1–20 to 1–15).

Request renaming of regulatory groups (e.g., fix typos, provide clarity).

Captures:

Requestor's name

Detailed instructions

Date of request

Requests are reviewed and actioned by Enterprise Compliance (e.g., KL team members).

5. Miscellaneous System Improvements
The Mapping Dashboard now lists all change codes since the last mapping exercise (not just the latest change code).

Additional columns have been added across various dashboards to provide more context and decision support to users during the mapping and validation processes.
