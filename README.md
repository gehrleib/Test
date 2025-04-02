// Select tbody rows, excluding 'no records' rows
    var tbodyRows = $('#master_DefaultContent_rts_ts7046_s7048_f20653srvgrid_ctl00 tbody tr').not('.rgNoRecords');
    console.log("Tbody Rows Found:", tbodyRows.length);

    var tbodyRowCount = 0;

    tbodyRows.each(function() {
        // Find the div within the current row whose ID *ends with* ':21738c'
        // Need to escape the colon for the selector
        let cellDiv = $(this).find("div[id$='\\:21738c']");

        // Check if the div was found and its text content (including children) is "Yes"
        if (cellDiv.length && cellDiv.text().trim() === "Yes") {
            tbodyRowCount++;
            console.log("Found 'Yes' in row:", $(this).attr('id')); // Optional: log which row matched
        }
    });

    console.log("Tbody Row Count (Yes values):", tbodyRowCount);
