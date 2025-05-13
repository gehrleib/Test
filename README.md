Title:
Revert Regulatory Content Overview Dashboard to Legacy Dashboard Technology for Stability

Story:
As a RegComp user,
I want the Regulatory Content Overview dashboard to reliably load and respond quickly,
So that I can access and review regulatory content without technical issues or delays.

Description:
RSA Archer introduced a new dashboard framework, and we adopted this for the Regulatory Content Overview dashboard during the software upgrade in June/July 2024.

However, in practice, the new dashboard technology has proven unstable:

Users occasionally encounter a failure to load, with the only workaround being to close the tab and reopen it.

This results in a poor user experience and undermines confidence in the system’s reliability.

Solution:

Revert the Regulatory Content Overview dashboard to use the legacy (old) dashboard technology.

This older framework is more responsive, stable, and does not suffer from loading issues.

Although a future software upgrade later this year may resolve the issue in the new dashboard engine, it will not meet our June 30th release/onboarding deadline.

Reverting ensures a stable experience in time for release and onboarding activities.

Acceptance Criteria:

 Regulatory Content Overview dashboard is converted back to the legacy dashboard format

 Dashboard loads reliably without requiring tab refresh or restart

 No loss of existing dashboard functionality or filters

 Ready and deployed in time for June 30 onboarding/release milestone

Notes:

If future updates resolve the issue, we may re-evaluate use of the newer dashboard tech in a later phase
