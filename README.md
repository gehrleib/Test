Option A: Tagging within Eclipse/MetricStream (E/M)

This approach requires the Assessable Unit information to be present within the E/M system before or during the tagging process. There are two proposed methods to get this AU data into E/M:

Method 1: API Integration

Process: The E/M system (or an associated process) would use an Application Programming Interface (API) to actively pull AU data.
Source: This data would come from a predefined report (presumably generated from EIM or another master source).
Requirements:
Technical expertise is needed to develop, configure, or leverage the necessary API connection.
The source system must expose the required AU data via an API endpoint compatible with the predefined report structure.
E/M must have the functionality to store the imported AU data.
Key Question: What level of detail does E/M need to store?
Just the Assessable Unit ID for basic linking?
Or does it require richer information like Line of Business, Theme, Country, Status, etc., for context or reporting within E/M? This needs clarification as it impacts storage and potentially the API/report design.
Method 2: XML File Drop via NAS

Process: A designated service ID (associated with the system generating AU data, likely EIM) would be granted access to write files to a specific Network Attached Storage (NAS) location. E/M would then need to monitor this location and ingest the files.
File Format: The data must be provided in a specific, system-generated XML format. This format is fixed and cannot be altered.
Requirements:
Granting the source system's service ID appropriate permissions to the NAS location.
E/M must be configured to read from the NAS location and specifically parse the provided, unchangeable XML format.
E/M must have the functionality to store the imported AU data.
Constraint: Lack of flexibility in the data format (fixed XML).
Key Question: Same as Method 1: What level of AU detail is contained in the XML, and what does E/M need to store (ID only vs. full details)?
Overall Consideration for Option A: Both methods under this option require E/M to have the capability to store AU information. The critical decision point is determining the necessary granularity of this stored data (ID vs. full details).

Option B: Tagging within EIM

This approach leverages EIM as the primary system for managing AU data and potentially the tagging process itself.

Process: Once an audit issue is identified (and potentially logged or referenced in EIM), specific users (e.g., auditors) would be granted permissions within EIM to directly edit the relevant Assessable Unit record to create the link or tag.
Assumptions:
Assessable Units already reside and are managed within EIM.
Audit Issues are either entered into EIM or can be easily referenced/linked from within EIM.
All primary reporting involving AUs and potentially their associated audit issues originates from EIM.
Requirements:
Modifying user roles and permissions within EIM to allow the designated users to edit AU records for tagging purposes.
Clear process definition for when and how this tagging occurs in EIM.
Advantages:
Perceived simplicity, as it utilizes the system where AUs already exist.
Avoids data duplication or synchronization issues between EIM and E/M regarding AUs.
Leverages existing reporting structures within EIM.
Implication: If this option is chosen, the need for E/M to store detailed AU information might be significantly reduced or eliminated for the purpose of tagging. E/M might only need a reference ID if any linkage back to EIM is required within E/M itself.
Summary of Considerations:

E/M Tagging (Option A): Requires data integration (API or File Drop), technical setup, and a decision on how much AU data to store in E/M. Potentially keeps audit-related work consolidated in E/M if that's the primary audit tool.
EIM Tagging (Option B): Leverages the existing AU repository and reporting system (EIM). Requires permission changes in EIM. Generally simpler from a data integration perspective, assuming EIM can accommodate the tagging workflow.
