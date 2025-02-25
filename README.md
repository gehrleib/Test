Currently, the files received from CALMA to RCM include the CRAU ID (formerly known as CRCP ID). However, for EIM, they require the ORMS Control ID. RCM sends both the ORMS Control ID and the CRAU ID to CALMA, meaning that a new file must be created for EIM with the ORMS Control ID.

We have confirmed that RCM receives two files: one containing the control ID and another with the assessable unit ID (previously known as Compliance Program ID). Moving forward for EIM, there should be a single file. Each issue must include at least the assessable unit. In cases where only a control ID was previously sent, the associated assessable unit and the ORMS Control ID should be provided. The reason for this is that the ORMS Control ID alone does not specify the appropriate assessable unit. 

For RCM, we did not need the assessable unit because we could look it up using the CRAU ID.
