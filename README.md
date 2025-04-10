I concur with Sri's assessment regarding the RegComp files; no immediate structural update is required, as we can filter using 'Non-Issue Identifier = Yes'.

To clarify our process for items flagged this way ('Non-Issue Identifier = Yes'): our system automatically closes them once they are ingested into RegComp. Their function is solely for logging purposes (containing limited fields: subject, description, root cause, source, related control, and assessable unit), and no further action is performed on them within the RegComp environment post-ingestion. This confirms the sufficiency of the current filtering approach.

Looking ahead, we anticipate receiving the updated root cause values utilized by EIM (presumably for actual issues requiring action).

Currently, we assign 'XYZ' as the issue source during ingestion for all items received from CALMA. Will this continue to be a static value? If so, please provide the specific value to be used. This value does not need to be included directly in the file, as we can apply it during our ingestion process.

Option 2 (Clear and Direct, Focused):

I agree with Sri – we don't need to change the RegComp files or structure right now because we can filter using 'Non-Issue Identifier = Yes'.

Just to explain our handling for items marked 'Yes': we automatically close these on our side after they're ingested into RegComp purely for logging. They only contain limited data (subject, description, root cause, source, control, unit), and no further action happens on them within RegComp. This confirms filtering works for now.

Going forward, we still expect to get the updated root cause values EIM uses (likely needed for the actual issues).

Regarding the issue source we assign during ingestion for everything received from CALMA: we currently use 'XYZ'. Is the plan to continue using a static value? If yes, please confirm the value we should use. We can handle this during ingestion, so it doesn't need to be in the file.
