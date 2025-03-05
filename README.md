Hey Cathy,

The 13 records where the annual decision was triggered a second time have been resolved. These assessable units have been reverted back to an "Approved" state, and the duplicate annual decision has been deleted.

The root cause of the issue was in our configuration. We had a date condition set for December 12 for the old process, which did not require 2LOD review to ensure the annual decision remained complete. The problem occurred due to a mismatch in how the system compared a datetime value with a date value, which only affected records that were closed between December 10 and December 12.
