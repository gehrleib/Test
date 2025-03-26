Jira Story: Enforce Completion of Sub-Assessments Before Risk Assessment Submission
Background
The Risk Assessment process requires the completion of several sub-assessments before submission. These include:

Business Profile Questionnaire

Local Regulatory Environment Questionnaire

Control Assessment

Regulatory Theme Checklist (Baseline Inherent Risk Rating)

To enhance the user experience and ensure compliance, the system will enforce completion of these sub-assessments before allowing submission. If any are incomplete, a message and a dynamic list of incomplete assessments will be displayed.

Requirements & Behavior
Validation Message for Incomplete Sub-Assessments

If one or more sub-assessments are incomplete, a message will appear:

"Note: The risk assessment requires that all assessments are marked complete before you can submit."

Below this message, a dynamic list will display the names of the incomplete sub-assessments.

Message Disappearance Upon Completion

Once all sub-assessments are marked as complete, the validation message and the list will disappear automatically.

Automatic Recalculation & Save

The system will attempt to automatically save the Risk Assessment upon completing a sub-assessment.

This triggers a recalculation, checking if all required assessments are complete.

If they are, the validation message will be removed without requiring a manual page refresh.

Implementation Steps
Modify the Risk Assessment Page Logic

Add logic to check the status of all sub-assessments when a user interacts with the Risk Assessment.

Display the validation message and the list of incomplete sub-assessments if necessary.

Enable Automatic Save & Recalculation

Implement an automatic save event when a sub-assessment status changes.

Ensure the system recalculates completion status without requiring the user to refresh the page.

User Experience Enhancements

Ensure the validation message is prominent but non-intrusive.

Make the list of incomplete sub-assessments easy to read and dynamically updated.

Testing Approach
Scenario 1: Attempt to submit the Risk Assessment when all sub-assessments are incomplete.

Expectation: The validation message and full list of required assessments appear.

Scenario 2: Complete one sub-assessment.

Expectation: The list updates dynamically to reflect remaining incomplete assessments.

Scenario 3: Complete all sub-assessments.

Expectation: The validation message and list disappear, and submission becomes possible.

Scenario 4: Verify automatic save functionality when completing a sub-assessment.

Assumptions & Considerations
The sub-assessments have clearly defined completion statuses that the system can check.

Automatic saving does not introduce performance issues or conflicts with user actions.

The system has appropriate permissions to modify the Risk Assessment based on sub-assessment completion.
