Establish EIM Root Cause Hierarchy Module and Ingestion

Story Title: Create "Root Cause" Module and Ingest Hierarchical Data from EIM

As a: System Administrator / Data Manager

I want: A new "Root Cause" module/data object created in the system that mirrors the hierarchical root cause structure from EIM, and an automated process to ingest and synchronize this data.

So that: We have a reliable, up-to-date, centralized source of standardized EIM root causes to be used in other modules like Non-Issue Exceptions.

Description:
To align with Enterprise Issue Management (EIM), we need to adopt their standard root cause classifications. EIM maintains a multi-level hierarchical structure for root causes.
This story involves:

Defining and creating the schema/structure for a new "Root Cause" module/table capable of storing hierarchical data (e.g., fields for ID, Name, Description, Parent ID, Hierarchy Level, Active Status).
Developing and implementing a recurring process (e.g., daily batch, API trigger) to ingest the root cause hierarchy from the EIM source system.
The ingestion process must correctly populate the new module, reflecting the parent-child relationships and levels defined in EIM. It should handle additions, updates, and potentially deactivations/removals of root causes from EIM.
Acceptance Criteria:

A new "Root Cause" data module/table exists with fields to store ID, Name, Description (optional), Parent ID (for hierarchy), Hierarchy Level, and an Active/Inactive status.
An automated ingestion process is implemented that connects to the EIM source (details TBD - API, file feed, DB link).
The ingestion process successfully populates the "Root Cause" module with data from EIM.
Parent-child relationships and hierarchy levels (Level 1, Level 2, Level 3, etc.) are correctly stored based on the EIM source data.
The process can synchronize changes from EIM (new root causes added, existing ones updated, potentially marking ones removed from EIM as inactive).
The process includes appropriate logging and error handling.
Data is queryable, allowing retrieval based on level (e.g., fetch all Level 2 root causes).
