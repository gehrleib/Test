Capture Mapped Assessable Units by Regional Segment on Attestation Completion

Story:
As a compliance or audit stakeholder,
I want each Mapping Attestation record to include a snapshot of assessable units that were mapped at the time of attestation for the specific regional segment,
So that I can clearly verify what was attested to without relying on the full RegGroup history log.

Description:
When a Mapping Attestation is completed:

The system must capture and store a snapshot of the assessable units that are mapped to the relevant RegGroup and belong to the attestation’s assigned regional segment.

This list of assessable units should be saved directly in the attestation record to support audit traceability and reduce the need to investigate RegGroup mapping history.

The snapshot is static and reflects the mappings only at the time of attestation.

This includes assessable units mapped through any method (standard mapping workflow, manual assignment, or system-generated rules).

Acceptance Criteria:

 Upon attestation completion, capture a list of assessable units mapped to the RegGroup and assigned to the attestation’s regional segment

 Only assessable units within the matching regional segment are included in the snapshot

 The snapshot is saved within the Mapping Attestation record and is immutable

 The list remains unchanged even if mappings are modified post-attestation

 This applies regardless of how the assessable units were added (standard mapping or manual assignment)

 Auditors and stakeholders can view this list without reviewing RegGroup mapping logs
