Title:
Standardize Field and Module Terminology to Align with CUBE Naming Conventions

Story:
As a user and administrator of RegComp,
I want the field, rule, and module naming conventions across the system to align more closely with CUBE terminology,
So that terminology is consistent, intuitive, and easier to maintain across platforms.

Description:
We need to perform a comprehensive renaming of levels, fields, and references in RegComp to match CUBE's structure. This involves updates to field names, level names, references, rules, and any hardcoded labels in rules/actions or UI.

Modules & Changes:

1. Authoritative Sources
Level 1: Rename “Regulator” → “Issuing Body”
Regulator ID → Issuing Body ID

Regulator Name → Issuing Body Name

Regulatory Status → Issuing Body Status

Level 2: Rename “Issuance” → “RegBook”
Level name: "Issuance" → "RegBook"

Regulator (reference) → Issuing Body

Issuance Name → RegBook Name

Issuance Status → RegBook Status

Issuance Type → RegBook Type

Issuance Date → RegBook Date

Override Issuance Country → Override RegBook Country

Issuance Country → RegBook Country

Issuance Country (Source) → RegBook Country (Source)

Issuance URL (CUBE) → RegBook URL (CUBE)

Issuance URL (Source) → RegBook URL (Source)

Issuance ID → RegBook ID

Reference field: Sections → renamed to RegGroups

Level 3: Rename “Section” → “RegGroup”
Level name: "Section" → "RegGroup"

Issuance (reference) → RegBook

Section Name → RegGroup Name

Section Status → RegGroup Status

Section Status (Temporary) → RegGroup Status (Temporary)

Section ID → RegGroup ID

Section URL (CUBE) → RegGroup URL (CUBE)

Section Applies to RBC → RegGroup Applies to RBC

Section Imposes Requirements on RBC → RegGroup Imposes Requirements on RBC

Reference field: Sub-Sections → renamed to Citations

Level 4: Rename “Sub-Section” → “Citation”
Level name: "Sub-Section" → "Citation"

Sub-Section ID → Citation ID

Sub-Section Name → Citation Name

Sub-Section URL (CUBE) → Citation URL (CUBE)

2. Rename “Section” to “RegGroup” Across These Modules:
Change Requests

Manual Attestation Request

Mapping Attestation

Material Changes

Validation

All fields, rules, and labels referencing “Section” in these modules should be renamed to “RegGroup” for consistency.

Acceptance Criteria:

 All levels renamed according to the mapping above

 All relevant fields renamed to match CUBE terminology

 Reference fields updated accordingly (e.g., Regulator → Issuing Body, Section → RegGroup)

 All modules listed reflect "RegGroup" instead of "Section" in field names, labels, rules, and reports

 Validation to ensure references and integrations (e.g., dashboards, reports, filters) are not broken by renaming

Notes:

These renaming changes may also affect rules, calculated fields, cross-references, and dashboards. They should be updated in coordination.

Ensure audit logs or historical data views continue to work with updated field names.
