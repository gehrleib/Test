Title:
Display Redline Changes and Version Metadata for Citations in Newly Published Groups

Story:
As a user reviewing regulatory group publications,
I want to see both redlined and clean versions of citation content along with the version date,
So that I can clearly identify what has changed in each citation and when.

Description:
When a Regulatory Group is newly published:

The current version of a citation is defined as the version provided as part of the published RegGroup.

The system will compare the current version against its immediate previous version for the purposes of generating a redline.

If multiple versions were published in close succession, only the most recent change will be shown in the redline.

The redline will be displayed for all citations tied to the published group that have a version greater than 1,
even if that citation was not modified in the current publication.

Two content fields will be maintained for each citation:

One showing the redlined version (current vs previous)

One showing the clean version (current only)

Each citation will also display its last updated date or version date for transparency.

Acceptance Criteria:

 The “current version” is based on the citation version included in the published Regulatory Group

 Redline comparison uses the immediate prior version of that citation

 Redline is displayed for all citations in the published group with version > 1

 Two content fields are stored/displayed: redlined and clean

 Each citation includes a visible version or last updated date

 Data is available in the UI and for export/reporting purposes

Notes:

A redline being present does not imply that the citation changed during the current group publication—only that the citation has a previous version available.

This supports auditability and simplifies review for downstream users.
