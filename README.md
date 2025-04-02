$(document).ready(function() {

    // --- Configuration ---
    // Ensure the 'assessmentCountId' variable is correctly defined
    // somewhere *before* this script runs. For example:
    // var assessmentCountId = '20653'; // Example ID part

    // --- Get Assessment Count from Span ---
    // Assuming assessmentCountId is defined above or globally
    var assessmentCountText = '';
    try {
        var assessmentCountSpan = $('span[id*="_f' + assessmentCountId + 'c"]');
        if (assessmentCountSpan.length) {
            assessmentCountText = assessmentCountSpan.text().trim();
            console.log("Assessment Count Text (from span):", assessmentCountText);
        } else {
            console.error("Assessment count span not found for ID part:", assessmentCountId);
            return; // Exit if the count span isn't found
        }
    } catch (e) {
        console.error("Error getting assessment count:", e);
        return; // Exit on error
    }

    // --- Count Rows in Table ---
    var tbodyRowCount = 0;
    try {
        // Select the specific table body - Check recommended for robustness
        var tableBody = $('#master_DefaultContent_rts_ts7046_s7048_f20653srvgrid_ctl00 tbody');

        // Check if the table body exists before trying to find rows in it
        if (!tableBody.length) {
             console.error("Table body not found! Cannot count rows. Selector:", '#master_DefaultContent_rts_ts7046_s7048_f20653srvgrid_ctl00 tbody');
             // If the table body is missing, we cannot proceed with counting rows.
             // Depending on desired logic, you might compare assessmentCountText to 0 here,
             // or simply exit. Exiting is often safer.
             return;
        }

        // Select data rows within that table body, excluding placeholder 'no records' rows
        var tbodyRows = tableBody.find('tr').not('.rgNoRecords');
        console.log("Tbody Data Rows Found:", tbodyRows.length);

        // Loop through each data row
        tbodyRows.each(function(index) {
            // Find the div for 'Complete Assessment' *within the current row*
            // using the "Attribute Ends With" selector. Escape the colon ':'.
            let cellDiv = $(this).find("div[id$='\\:21738c']");

            // Check if the div was found and its *combined text content* is "Yes"
            if (cellDiv.length && cellDiv.text().trim() === "Yes") {
                tbodyRowCount++;
            }
        });

        console.log("Calculated Tbody Row Count (Yes values):", tbodyRowCount);

    } catch (e) {
        console.error("Error counting table rows:", e);
        return; // Exit on error during table processing
    }

    // --- Compare Counts and Trigger Action ---
    try {
        // Assuming assessmentCountText is always a string representing a number.
        // Convert it to a number for comparison.
        var assessmentCountNumber = parseInt(assessmentCountText, 10);

        console.log("Comparing Span Count (parsed as number):", assessmentCountNumber, "with Table 'Yes' Count:", tbodyRowCount);

        // Perform the comparison
        if (assessmentCountNumber !== tbodyRowCount) {
            console.warn("MISMATCH! Clicking apply button.");
            // Uncomment the line below when ready to enable the click action
            // $("#master_btnApply").click();
        } else {
            console.log("Counts match. No action needed.");
        }
    } catch (e) {
        console.error("Error during comparison or button click:", e);
    }

});
