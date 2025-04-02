/**
 * Counts the number of rows within a specific table's tbody where a div,
 * identified by a specific ID ending, contains the text "Yes".
 *
 * @param {object} config - Configuration object for the table/column.
 * @param {string} config.checkName - A descriptive name for this table/column (for logging).
 * @param {string} config.tableBodySelector - jQuery selector for the specific table's tbody (e.g., '#table1_id tbody').
 * @param {string} config.columnIdEnding - The ending part of the target div's ID within table rows (e.g., '\\:21738c'). Must escape special characters like ':'.
 * @returns {number} - The count of rows containing "Yes" in the specified column, or 0 if errors occur or table/elements aren't found.
 */
function countYesInTable(config) {
    console.log(`--- Counting 'Yes' in: ${config.checkName} ---`);
    let yesCount = 0; // Initialize count for this specific table

    try {
        var tableBody = $(config.tableBodySelector);

        if (!tableBody.length) {
            // Log error but return 0, as a missing table contributes 0 to the total sum
            console.error(`[${config.checkName}] Table body not found! Selector: ${config.tableBodySelector}. Returning count 0.`);
            return 0;
        }

        var tbodyRows = tableBody.find('tr').not('.rgNoRecords');
        // Log how many rows are being checked, not the final count yet
        console.log(`[${config.checkName}] Found ${tbodyRows.length} data rows in ${config.tableBodySelector} to check.`);

        tbodyRows.each(function() {
            // Find the div within the current row whose ID *ends with* the specified pattern.
            let cellDiv = $(this).find(`div[id$='${config.columnIdEnding}']`);
            if (cellDiv.length && cellDiv.text().trim() === "Yes") {
                yesCount++;
            }
        });

        console.log(`[${config.checkName}] Counted ${yesCount} 'Yes' values for column ending '${config.columnIdEnding}'.`);

    } catch (e) {
        // Log error but return 0, as errors prevent accurate counting for this table
        console.error(`[${config.checkName}] Error counting 'Yes' values:`, e);
        return 0;
    }

    return yesCount; // Return the count for this table
}

// --- Document Ready ---
$(document).ready(function() {

    console.log("Document ready. Initializing assessment count check...");

    // --- Configuration ---
    const singleAssessmentCountId = "20653"; // The unique ID part for the SINGLE assessment count span
    const mainButtonSelector = "#master_btnApply"; // The SINGLE button to click if totals mismatch

    // --- 1. Get Single Assessment Count ---
    let assessmentCountNumber = 0; // Default to 0
    let assessmentCountText = '';
    try {
        const assessmentSpanSelector = `span[id*="_f${singleAssessmentCountId}c"]`;
        const assessmentCountSpan = $(assessmentSpanSelector);

        if (assessmentCountSpan.length) {
            assessmentCountText = assessmentCountSpan.text().trim();
            assessmentCountNumber = parseInt(assessmentCountText, 10);

            // Validate parsing
            if (isNaN(assessmentCountNumber)) {
                 console.error(`Assessment count text "${assessmentCountText}" from ${assessmentSpanSelector} is not a valid number. Aborting checks.`);
                 // Optionally disable the button or show a user message here
                 return; // Stop script execution if count is invalid
            }
            console.log(`Successfully retrieved Assessment Count: ${assessmentCountNumber} (from span ${assessmentSpanSelector})`);
        } else {
            console.error(`Assessment count span not found! Selector: ${assessmentSpanSelector}. Aborting checks.`);
            // Optionally disable the button or show a user message here
            return; // Stop script execution if span is missing
        }
    } catch (e) {
        console.error(`Critical error getting assessment count:`, e);
        return; // Stop script execution on critical error
    }


    // --- 2. Define Table/Column Configurations ---
    // Note: No assessmentCountId needed here anymore
    const table1Config = {
        checkName: "Table A - Column 1", // Descriptive name
        tableBodySelector: "#table_A_id tbody", // Selector for the first table's body
        columnIdEnding: "\\:11111c"    // Ending ID part for the relevant column (escape colon)
    };

    const table2Config = {
        checkName: "Table B - Assessments",
        tableBodySelector: "#master_DefaultContent_rts_ts7046_s7048_f20653srvgrid_ctl00 tbody", // Example from original prompt
        columnIdEnding: "\\:21738c"    // Example from original prompt (escape colon)
    };

    const table3Config = {
        checkName: "Table C - Status",
        tableBodySelector: "#another_table_grid_ctl00 tbody", // Selector for the third table's body
        columnIdEnding: "\\:33333c"    // Ending ID part for the relevant column (escape colon)
    };


    // --- 3. Calculate Total 'Yes' Count Across Tables ---
    let totalYesCount = 0;
    console.log("Starting summation of 'Yes' counts across tables...");

    totalYesCount += countYesInTable(table1Config);
    totalYesCount += countYesInTable(table2Config);
    totalYesCount += countYesInTable(table3Config);

    console.log(`Summation complete. Total 'Yes' count across all checked tables: ${totalYesCount}`);


    // --- 4. Final Comparison and Action ---
    console.log(`Final Comparison: Assessment Count (${assessmentCountNumber}) vs. Total 'Yes' Count (${totalYesCount})`);
    if (assessmentCountNumber !== totalYesCount) {
        console.warn(`MISMATCH DETECTED! Assessment count (${assessmentCountNumber}) does not equal total 'Yes' count (${totalYesCount}). Clicking button: ${mainButtonSelector}`);
        try {
            // Uncomment the line below when ready to enable the click action
            // $(mainButtonSelector).click();
            console.log(`Attempted to click button: ${mainButtonSelector}`); // Log the attempt
        } catch(e) {
            console.error(`Error clicking button ${mainButtonSelector}:`, e);
        }
    } else {
        console.log("Counts match. No button click needed.");
    }

    console.log("All checks processed.");

});
