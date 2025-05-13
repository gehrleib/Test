Title:
Prompt for Mapping/Attestation Review When Validation Responses Remain Unchanged

Story:
As a validator performing multiple rounds of validation,
I want to be prompted when responses remain unchanged from a previous validation,
So that I can decide whether a new mapping/attestation should still be required due to a material change in content.

Description:
When a second, third, or subsequent validation is performed and the validator's responses are identical to those provided in the previous validation round:

The system should present an additional checkbox asking whether the mappers should still be required to perform a new mapping/attestation.

This allows the validator to flag cases where, despite no change in their answers, the underlying citation content may have materially changed, warranting a fresh mapping.

Important Note:

This only applies when validation responses are the same as in the previous round.

If any responses have changed, the system already automatically triggers a new mapping/attestation.

Example: If the Regulatory Theme is changed, assessable units tied to the old theme are automatically removed, requiring reassignment to the new theme.

Acceptance Criteria:

 When validation responses remain unchanged from the previous round, a checkbox appears:
“Require new mapping/attestation due to a material change in content”

 This checkbox is only shown in cases where responses are identical to the previous validation

 If the checkbox is selected, the system will initiate a new mapping/attestation process

 If the checkbox is left unchecked, no new mapping will be triggered

 If responses differ from the previous validation, the checkbox is not shown, and the system triggers mapping/attestation automatically (as it does today)

 The checkbox selection is recorded and auditable

Notes:

This provides flexibility for edge cases where the regulatory meaning has changed without affecting validation answers (e.g., wording or scope clarification).

Helps reduce unnecessary mapping efforts while ensuring compliance integrity.

