Here’s a screenshot that better illustrates the data structure. We have three levels:

The regulator (or issuing body)
The issuance (or the Book)
The section (or Group)
Currently, the segment is tied to the regulator, the country is linked to the book, and the theme is associated with the section. These three fields determine which assessable units can be selected when a section is applied to impact RBC.

This means that changes to segments can affect all issuances and their groups. For example, adding a new segment would trigger a new mapping attestation for every group across all issuances.

To align more closely with RegInsight and RegFlow, I’ve proposed moving the segment from the regulator to the issuance. This would allow for more granular control over impacted sections but may require updating more books. Currently, there are approximately 202 regulators and 2,748 issuances.
