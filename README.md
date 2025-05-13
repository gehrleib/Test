Handle Empty API Responses as Errors to Prevent Unintended RegGroup Archiving and Assessable Unit Delinking

Type: Bug / Technical Story

Story:
As a system integrator,
I want the script to treat empty API responses as errors instead of valid results,
So that we avoid mistakenly archiving RegGroups and delinking assessable units due to false assumptions of deletion.

Description:
Currently, we perform an API call to fetch RegGroup data. In some cases, the API call is technically successful (e.g., returns HTTP 200) but the body of the response is empty.

Our current logic interprets this empty response as meaning the RegGroup no longer exists (e.g., deleted), which triggers:

The automatic archiving of the RegGroup

The automatic delinking of any assessable units associated with that RegGroup

This behavior is incorrect and introduces risk of data loss or false compliance gaps.

Fix Required:

Update the script to treat an empty response as an error, even if the HTTP status is 200

When an empty response is detected:

Log the event as an error (e.g., “Empty response received for RegGroup ID: XYZ”)

Do not proceed with archiving or delinking

Stop the script (or skip to next item, depending on broader context)

Acceptance Criteria:

 Script checks for empty body/content even when HTTP status is 200

 If response is empty:

 Log the issue with the relevant RegGroup ID

 Do not archive the RegGroup

 Do not delink assessable units

 Stop or safely skip processing for that RegGroup (based on processing mode)

 Normal processing continues for valid (non-empty) responses

 Regression tested to ensure RegGroups are only archived when truly unavailable
