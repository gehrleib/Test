Title:
Auto-Create Draft Validation for Previously Validated RegGroups Upon New Publication

Story:
As a validator,
I want the system to automatically generate a draft validation when a previously validated RegGroup is re-published,
So that I can quickly review changes (via redlines, version dates, etc.) and confirm whether any updates or downstream actions are required.

Description:
When a RegGroup is newly published, and a validation has previously occurred for that RegGroup and region:

The system should automatically create a new validation record in “Draft” status, carrying over the responses from the most recent completed validation.

This allows validators to perform a “light touch” review, focusing only on redline changes, citation update dates, or other material updates.

If no changes are needed, the validator can simply submit the draft as-is.

Even if the responses remain unchanged, the validator may still choose to trigger a mapping/attestation, as defined in a separate story.

These draft validations should appear in a distinct dashboard bucket, separate from validations for RegGroups that have not been validated before.

The RegGroup record should also clearly show the publication date, which can be used alongside citation-level version dates and redlines to help inform the review.

Acceptance Criteria:

 When a RegGroup is published and has a prior completed validation, a new validation record is auto-created in Draft status

 Draft validation pre-populates with responses from the most recent prior validation

 The associated RegGroup's publication date is saved and visible in the record

 Draft validations appear in a separate bucket on the dashboard, e.g., "Previously Validated RegGroups – Requires Review"

 New (never-before validated) RegGroups appear under “New RegGroups – Require Initial Validation”

 Validators can review redlines, citation version dates, and publication date to decide if changes are needed

 Validators can choose to submit with no changes, or update responses and/or flag the need for a new mapping/attestation
