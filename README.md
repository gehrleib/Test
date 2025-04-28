1. Validation Form Changes
Context:
In the current RegComp Validation form, users are asked:

Whether a regulatory group applies and impacts RBC.

To select the appropriate Regulatory Themes.

Proposed Change:
Given that CUBE already identifies regulatory groups that apply and impact RBC — and manages archival (via tag or deletion) when they no longer do — asking whether groups apply/impact within RegComp may no longer be necessary.

Going forward, the focus would solely be on ensuring the Regulatory Theme is captured.

Options for Management:

Option 1:

Maintain a dashboard that highlights regulations missing a Regulatory Theme.

Repurpose the "Validator" role so that its only responsibility is to manage and update the Regulatory Theme field.

Option 2:

Have CUBE tag the Regulatory Theme (Level 3) directly in their system.

RegComp would ingest the Regulatory Theme tag from CUBE.

Challenges with Option 2:

CUBE must maintain an up-to-date list of Regulatory Themes, including handling renames, additions, and deletions.

There are ongoing discussions about migrating from Regulatory Themes to Risk Classifications.

CUBE would need to support the migration to Risk Classifications in alignment with our project timelines.

2. Permissions in RegComp
Default Access:

All RBC employees have read access to CUBE-provided regulatory data within RegComp.

Exception:

RBC employees cannot see tagged Assessable Units unless:

They are explicitly assigned/mentioned on the Assessable Unit.
