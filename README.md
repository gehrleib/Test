Allow Segment Override During Validation and Trigger Mapping When Segment Changes

Story:
As a validator,
I want the ability to override the Issuing Body’s segment during validation (with rationale),
So that I can ensure the correct regional segment is applied for validation and mapping purposes, even if the Issuing Body’s default segment is not appropriate.

Description:
The segment value currently resides on the Issuing Body and this will remain the source of truth. However, during the completion of a Validation, the following changes are required:

The validation form will display the segment from the associated Issuing Body as the default.

A checkbox option will be available to allow the validator to override the default segment.

If selected, the user must provide a rationale for the override.

This overridden segment value will take precedence over the Issuing Body’s segment.

The override is specific to that validation instance.

If a new validation is performed and the override checkbox is not selected, the system will default back to using the Issuing Body’s current segment.

Impact on Mapping/Attestation:

Changes to the Issuing Body’s segment already trigger a new mapping/attestation – this behavior should remain unchanged.

A new override of the segment during validation must also trigger mapping/attestation for the applicable regional segment.

Acceptance Criteria:

 Validation screen displays the current Issuing Body’s segment by default

 Validator has an option to override the segment via checkbox

 If override is selected, a required rationale field appears

 The override segment value is stored and takes precedence over the Issuing Body segment

 If no override is selected in future validations, the system reverts to using the current Issuing Body’s segment

 Any change to the segment (whether via override or Issuing Body update) triggers a new mapping/attestation process

 Override status and rationale are auditable and visible within the validation record

Notes:

Overrides help address edge cases where the regulatory ownership or application differs from the Issuing Body’s default.
