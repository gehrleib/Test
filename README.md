Hi Matt,

I'm writing to confirm my understanding of the process duplication issue we're trying to resolve regarding segment identification in RegComp and to discuss potential solutions.

Problem:
My understanding is that segments impacted by regulatory changes are identified during the impact assessment (informed by horizon scanning) at the Issuance/Book level (Level 2). However, the corresponding "segment" field in RegComp is currently configured at the higher Regulator level (Level 1). This misalignment prevents accurate pre-population from CUBE, as applying a segment at Level 1 would incorrectly include groups or citations not relevant to that specific segment assessed at Level 2.

Proposed Solution:
To eliminate this duplication and enable correct pre-population, we propose relocating the "segment" field in RegComp from Level 1 (Regulator) to Level 2 (Issuance/Book). This aligns the field with the granularity of the impact assessment and CUBE data.

Options for Overriding Segment Value:
Regarding overrides, we have a few options depending on the desired granularity:

Allow Enterprise Compliance to override the segment value at the Issuance/Book level (L2).
Allow Validators to override the segment value at the Group/Citation level (L3), potentially integrated with their validation task.
Implement both options.
Question on Validation Process:
Separately, I'm unclear on the current status of the RegComp validation step. This is where users determine applicability to RBC, requirement imposition, and theme assignment for citation groups. If our process evolves to only create groups in RegComp that do apply and impose requirements, will the validation steps for applicability and imposition still be needed, or will the focus shift solely to assigning the theme?

Could we connect to confirm this understanding and discuss the best path forward for both the segment field location and the validation scope?
