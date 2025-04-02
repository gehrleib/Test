/**
 * Checks if the count displayed in a span matches the number of rows
 * in a specific table column containing "Yes". Clicks a button if counts mismatch.
 *
 * @param {object} config - Configuration object for the check.
 * @param {string} config.checkName - A descriptive name for this check (for logging).
 * @param {string} config.assessmentCountId - The unique part of the ID for the assessment count span (e.g., '20653').
 * @param {string} config.tableBodySelector - jQuery selector for the specific table's tbody (e.g., '#table1_id tbody').
 * @param {string} config.columnIdEnding - The ending part of the target div's ID within table rows (e.g., '\\:21738c'). Must escape special characters like ':'.
 * @param {string} config.buttonSelector - jQuery selector for the button to click on mismatch (e.g., '#master_btnApply').
 * @returns {boolean} - True if counts match or check couldn't fully complete due to errors, False if counts mismatch.
 */
function checkTableCount(config) {
    console.log(`--- Starting Check: ${config.checkName} ---`);
    let countsMatch = true; // Assume match initially, set to false on mismatch

    // --- 1. Get Assessment Count from Span ---
    var assessmentCountText = '';
    try {
        // Construct the full selector for the span
        var assessmentSpanSelector = `span[id*="_f${config.assessmentCountId}c"]`;
        var assessmentCountSpan = $(assessmentSpanSelector);

        if (assessmentCountSpan.length) {
            assessmentCountText = assessmentCountSpan.text().trim();
            // Assuming the text is always a number based on previous request
            console.log(`[${config.checkName}] Assessment Count Text (from span ${assessmentSpanSelector}):`, assessmentCountText);
        } else {
            console.error(`[${config.checkName}] Assessment count span not found! Selector: ${assessmentSpanSelector}`);
            return true; // Cannot perform check, return true to avoid false mismatch trigger
        }
    } catch (e) {
        console.error(`[${config.checkName}] Error getting assessment count:`, e);
        return true; // Cannot perform check
    }

    // --- 2. Count Rows in Table ---
    var tbodyRowCount = 0;
    try {
        var tableBody = $(config.tableBodySelector);

        if (!tableBody.length) {
            console.error(`[${config.checkName}] Table body not found! Selector: ${config.tableBodySelector}`);
            // If the table body is missing, we can't count. Decide how to handle.
            // Option 1: Treat as mismatch if assessmentCount > 0
            // Option 2: Log error and treat as 'match' to avoid potentially incorrect button click. (Safer)
            return true; // Treat as cannot-complete / no-mismatch found
        }

        var tbodyRows = tableBody.find('tr').not('.rgNoRecords');
        console.log(`[${config.checkName}] Tbody Data Rows Found in ${config.tableBodySelector}:`, tbodyRows.length);

        tbodyRows.each(function() {
            // Find the div within the current row whose ID *ends with* the specified pattern.
            let cellDiv = $(this).find(`div[id$='${config.columnIdEnding}']`);
            if (cellDiv.length && cellDiv.text().trim() === "Yes") {
                tbodyRowCount++;
            }
        });
        console.log(`[${config.checkName}] Calculated Tbody Row Count ('Yes' values in column ending '${config.columnIdEnding}'):`, tbodyRowCount);

    } catch (e) {
        console.error(`[${config.checkName}] Error counting table rows:`, e);
        return true; // Cannot perform check
    }

    // --- 3. Compare Counts and Trigger Action ---
    try {
        // Assuming assessmentCountText is always a string representing a number.
        var assessmentCountNumber = parseInt(assessmentCountText, 10);

        console.log(`[${config.checkName}] Comparing Span Count (parsed as number): ${assessmentCountNumber} with Table 'Yes' Count: ${tbodyRowCount}`);

        if (assessmentCountNumber !== tbodyRowCount) {
            countsMatch = false; // Mismatch found!
            console.warn(`[${config.checkName}] MISMATCH! Span: ${assessmentCountNumber}, Table: ${tbodyRowCount}. Clicking button: ${config.buttonSelector}`);
            // Uncomment the line below when ready to enable the click action
            // $(config.buttonSelector).click();
        } else {
            console.log(`[${config.checkName}] Counts match.`);
        }
    } catch (e) {
        console.error(`[${config.checkName}] Error during comparison or button click:`, e);
        return true; // Error occurred, treat as cannot-complete
    }

    console.log(`--- Finished Check: ${config.checkName} ---`);
    return countsMatch; // Return true if matched, false if mismatched
}

// --- Document Ready ---
$(document).ready(function() {

    console.log("Document ready. Starting table count checks...");

    // --- Configuration for the Checks ---
    // Replace placeholders with your actual IDs and selectors

    const check1Config = {
        checkName: "Assessment Type A", // Descriptive name
        assessmentCountId: "10001",     // ID part for the first count span
        tableBodySelector: "#table_A_id tbody", // Selector for the first table's body
        columnIdEnding: "\\:11111c",   // Ending ID part for the relevant column in table A (escape colon)
        buttonSelector: "#master_btnApply" // Button to click if mismatch
    };

    const check2Config = {
        checkName: "Assessment Type B",
        assessmentCountId: "10002",     // ID part for the second count span
        tableBodySelector: "#master_DefaultContent_rts_ts7046_s7048_f20653srvgrid_ctl00 tbody", // Example from original prompt
        columnIdEnding: "\\:21738c",   // Example from original prompt (escape colon)
        buttonSelector: "#master_btnApply"
    };

    const check3Config = {
        checkName: "Assessment Type C",
        assessmentCountId: "10003",     // ID part for the third count span
        tableBodySelector: "#another_table_grid_ctl00 tbody", // Selector for the third table's body
        columnIdEnding: "\\:33333c",   // Ending ID part for the relevant column in table C (escape colon)
        buttonSelector: "#master_btnApply"
    };

    // --- Execute the Checks ---
    // You can optionally track the overall status if needed
    let overallMatch = true;

    overallMatch &= checkTableCount(check1Config); // Use &= to set overallMatch to false if any check fails
    overallMatch &= checkTableCount(check2Config);
    overallMatch &= checkTableCount(check3Config);

    // Optional: Log final status
    if(overallMatch) {
        console.log("All table count checks completed successfully and matched.");
    } else {
        console.warn("One or more table count checks resulted in a mismatch.");
    }

});
