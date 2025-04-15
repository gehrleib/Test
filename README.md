Title: Implement Daily Ingestion of Linked EIM Issues into RegComp EIM Module

Story Type: Story

Description:

As a RegComp User/Compliance Officer,
I want a daily automated process established to ingest specific issue data from the source Enterprise Issue Management (EIM) system into RegComp's EIM module,
So that I have synchronized visibility within RegComp of EIM issues that are actively linked to Assessable Units or Exams, based on the specifications in the interface agreement.

Background:
RegComp needs visibility into specific issues managed in the central Enterprise Issue Management (EIM) system. This story covers the creation of a daily ingestion process to synchronize these issues into the RegComp EIM module, but only for those issues relevant to RegComp activities (linked to Assessable Units or Exams). This data will be used for reporting and context within RegComp.

Acceptance Criteria:

A new automated process is created that runs daily.
The process connects to the source EIM system/data feed as required.
The process ingests data for all fields specified in the attached Interface Agreement ([Link to or name of Interface Agreement document]).
Data is correctly mapped from the source fields to the corresponding fields within the RegComp EIM module structure.
Filtering: The process correctly identifies and ingests only those issues from the EIM source that are currently linked to at least one Assessable Unit OR at least one Exam.
Issues from the EIM source that are not linked to an Assessable Unit or Exam are excluded and not ingested.
Synchronization (New/Update):
If an EIM issue meets the criteria and does not yet exist in the RegComp EIM module, it is created.
If an EIM issue meets the criteria and already exists in the RegComp EIM module, its data (as per the interface agreement fields) is updated to match the latest information from the source.
Synchronization (Removal from Scope):
If an issue was previously ingested (it met the criteria on a prior run) but no longer meets the filtering criteria on the current run (e.g., links to all AUs/Exams were removed in the source EIM system), its status within the RegComp EIM module must be updated to "Cancelled" (or the agreed-upon equivalent status).
This "Cancelled" status in RegComp applies even if the issue remains open/active in the source EIM system; it reflects that the issue is no longer relevant based on the RegComp filtering criteria.
The daily process runs successfully without manual intervention.
Adequate logging is implemented to track the execution of the daily process, including start/end times, number of records processed (ingested, updated, marked cancelled), and any errors encountered.
