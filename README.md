Refactor CALMA to Non-Issue Exceptions Integration in RegComp

Story:
As a system administrator,
I want to refactor the integration between CALMA and Non-Issue Exceptions in RegComp,
So that only relevant records are ingested and properly mapped to internal metadata, ensuring consistency and auditability.

Description:
We need to refactor the existing integration that ingests data from CALMA into the Non-Issue Exceptions module within RegComp.

Ingestion Logic:
The source file contains a field called Non_Issue_Identifier.

Only records where Non_Issue_Identifier = "Yes" will be ingested into RegComp.

The integration must support ingesting the following fields:

Subject

Description

Root Cause

Control or Assessable Unit (only one will be present depending on the file structure)

Field Population Rules:
Originating Practice will always be set to "Compliance Monitoring & Testing"

Segment, Line of Business, and Regulatory Theme will be derived from the tagged Control or Assessable Unit, depending on which is present
