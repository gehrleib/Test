Currently, the Next Control Test Year (Final) field on the 'Control Result for Assessable Unit' is a Value List. This needs to be converted to a Numeric field type to allow for better calculations and consistency, similar to how the Override field functions.

This change involves:

Archiving the existing Next Control Test Year (Final) (Value List) field.
Creating a new Next Control Test Year (Final) field with a Numeric type.
Implementing calculation logic for the new field: The value should always be the greater of the System calculated next test year and the Override next test year.
New Next Control Test Year (Final) = MAX( [System Next Test Year], [Override Next Test Year] )
Implementing overnight logic for the separate Override field: If an Override value is entered that is less than or equal to the System value, this Override value should be cleared/removed by an overnight process. (Real-time validation isn't feasible due to inline edit behaviour).
Updating the M&T Plan (both Master and Addendums) to display the new numeric Next Control Test Year (Final) field in the relevant column, replacing the old field reference.


Reporting: Users with custom reports (e.g., saved searches, dashboards, exported reports) that utilize the Next Control Test Year (Final) field will need to manually update their reports to reference the new field ID.
API Integration: Any APIs (internal or external) currently reading or writing to the old Next Control Test Year (Final) field will be impacted and require updates to use the new field ID and accommodate the numeric type.
