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
            console.error(`[${config.checkName}] Table body not found! Selector: ${config.tableBodySelector}. Returning count 0.`);
            return 0;
        }
        var tbodyRows = tableBody.find('tr').not('.rgNoRecords');
        console.log(`[${config.checkName}] Found ${tbodyRows.length} data rows in ${config.tableBodySelector} to check.`);
        tbodyRows.each(function() {
            let cellDiv = $(this).find(`div[id$='${config.columnIdEnding}']`);
            if (cellDiv.length && cellDiv.text().trim() === "Yes") {
                yesCount++;
            }
        });
        console.log(`[${config.checkName}] Counted ${yesCount} 'Yes' values for column ending '${config.columnIdEnding}'.`);
    } catch (e) {
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
    // Button selectors are now handled in the final action block

    // --- 1. Get Single Assessment Count ---
    let assessmentCountNumber = 0; // Default to 0
    let assessmentCountText = '';
    try {
        const assessmentSpanSelector = `span[id*="_f${singleAssessmentCountId}c"]`;
        const assessmentCountSpan = $(assessmentSpanSelector);
        if (assessmentCountSpan.length) {
            assessmentCountText = assessmentCountSpan.text().trim();
            assessmentCountNumber = parseInt(assessmentCountText, 10);
            if (isNaN(assessmentCountNumber)) {
                 console.error(`Assessment count text "${assessmentCountText}" from ${assessmentSpanSelector} is not a valid number. Aborting checks.`);
                 return;
            }
            console.log(`Successfully retrieved Assessment Count: ${assessmentCountNumber} (from span ${assessmentSpanSelector})`);
        } else {
            console.error(`Assessment count span not found! Selector: ${assessmentSpanSelector}. Aborting checks.`);
            return;
        }
    } catch (e) {
        console.error(`Critical error getting assessment count:`, e);
        return;
    }

    // --- 2. Define Table/Column Configurations ---
    const table1Config = {
        checkName: "Table A - Column 1",
        tableBodySelector: "#table_A_id tbody",
        columnIdEnding: "\\:11111c"
    };
    const table2Config = {
        checkName: "Table B - Assessments",
        tableBodySelector: "#master_DefaultContent_rts_ts7046_s7048_f20653srvgrid_ctl00 tbody",
        columnIdEnding: "\\:21738c"
    };
    const table3Config = {
        checkName: "Table C - Status",
        tableBodySelector: "#another_table_grid_ctl00 tbody",
        columnIdEnding: "\\:33333c"
    };

    // --- 3. Calculate Total 'Yes' Count Across Tables ---
    let totalYesCount = 0;
    console.log("Starting summation of 'Yes' counts across tables...");
    totalYesCount += countYesInTable(table1Config);
    totalYesCount += countYesInTable(table2Config);
    totalYesCount += countYesInTable(table3Config);
    console.log(`Summation complete. Total 'Yes' count across all checked tables: ${totalYesCount}`);

    // --- 4. Final Comparison and Conditional Action ---
    console.log(`Final Comparison: Assessment Count (${assessmentCountNumber}) vs. Total 'Yes' Count (${totalYesCount})`);

    if (assessmentCountNumber !== totalYesCount) {
        console.warn(`MISMATCH DETECTED! Assessment count (${assessmentCountNumber}) does not equal total 'Yes' count (${totalYesCount}). Checking for action buttons...`);

        const applyButtonSelector = "#master_btnApply";
        const recalcButtonSelector = "#master_btnRecalculate";
        let buttonClicked = false;

        try {
            // Check for Apply button first
            const $applyButton = $(applyButtonSelector);
            if ($applyButton.length > 0 && $applyButton.is(':visible')) {
                console.log(`Found available button: ${applyButtonSelector}. Clicking it.`);
                // Uncomment the line below when ready to enable the click action
                // $applyButton.click();
                buttonClicked = true;
                console.log(`Attempted to click button: ${applyButtonSelector}`);
            } else {
                 console.log(`Button ${applyButtonSelector} not found or not visible. Checking for ${recalcButtonSelector}.`);
                 // If Apply button wasn't available, check for Recalculate button
                 const $recalcButton = $(recalcButtonSelector);
                 if ($recalcButton.length > 0 && $recalcButton.is(':visible')) {
                     console.log(`Found available button: ${recalcButtonSelector}. Clicking it.`);
                     // Uncomment the line below when ready to enable the click action
                     // $recalcButton.click();
                     buttonClicked = true;
                     console.log(`Attempted to click button: ${recalcButtonSelector}`);
                 } else {
                     console.log(`Button ${recalcButtonSelector} not found or not visible either.`);
                 }
            }

            if (!buttonClicked) {
                console.warn("Mismatch occurred, but neither Apply nor Recalculate button was found or visible. No action taken.");
            }

        } catch(e) {
            console.error(`Error during button check or click logic:`, e);
        }

    } else {
        console.log("Counts match. No button click needed.");
    }

    console.log("All checks processed.");

});
