Hi Cathy,

I'm writing to clarify the annual decision processing.

Units with a Next Assessment Date in January 2025 (specifically, January 8-25) were not scheduled for annual decisions until December 16th (23 days later). The December 10, 2024, implementation caused these units to be flagged as overdue and trigger assessments immediately, which is the expected outcome.
We've identified a bug that caused 13 assessable units to undergo a second annual decision between December 10-12. This was unintended. I've created an incident ticket to address this. The root cause was a date discrepancy in the 2LOD review condition; it was using December 12th instead of December 10th.
