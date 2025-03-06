There’s an update on the root cause. I initially thought the issue was due to the implementation date, as my plan indicated December 10, but the actual implementation was on December 12—matching the configuration—so the date was not the problem. Instead, the issue arose from how the software compares a datetime (Submission Date) with a date (Condition) value.

As a result, some annual decisions completed on December 11-12 were marked as both complete and incomplete, triggering a new annual decision. The fix was to update the condition from <= DATETIMEVALUE("12/12/2024") to < DATETIME("12/13/2024"). While the change appears minor, it corrected the behavior.

All changes were tested by both Quality Assurance and the business, but this would have been difficult to catch in testing since we may not have had data replicating this exact scenario.

There was no significant material impact, as the annual decision was simply re-generated, and users were asked to complete it again.
