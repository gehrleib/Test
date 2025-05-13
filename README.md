Treat Empty API Response as an Error to Prevent Incorrect RegGroup Archiving

Story / Bug:
As a system administrator,
I want to prevent RegGroups from being incorrectly archived when an API returns an empty response,
So that assessable units are not mistakenly delinked due to false assumptions about RegGroup availability.

Description:
Currently, when an API call to retrieve a RegGroup returns an empty response, the script incorrectly interprets this as the RegGroup being unavailable or deleted.

This triggers a false archive of the RegGroup and leads to assessable units being automatically delinked, creating downstream data integrity issues.

To resolve this:

The script should be updated to treat empty responses as an error condition, rather than a valid "not found" result.

If an empty response is detected, the script must log an error and stop execution, rather than proceeding with archiving or delinking actions.

Acceptance Criteria:

 If the API call is successful but returns an empty payload/body, the script treats it as an error

 The script logs a clear error message (e.g., "Empty API response for RegGroup [ID] – skipping archive")

 The script halts further processing for that RegGroup

 No archiving or assessable unit delinking is triggered from empty responses

 RegGroups are only archived if the API explicitly indicates deletion or unavailability

Notes:

This change safeguards against false-positive deletions caused by temporary API issues, rate-limiting, or content delays.

Consider adding retry logic or alerting if repeated empty responses occur for the same RegGroup.
