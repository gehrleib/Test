$(document).ready(function() {
    var consultCount = $('span[id*="_f' + assessmentCountId + 'c"]').text().trim();
    console.log("Consult Count:", consultCount);

    // Select tbody rows, excluding 'no records' rows
    var tbodyRows = $('#master_DefaultContent_rts_ts7046_s7048_f20653srvgrid_ctl00 tbody tr').not('.rgNoRecords');
    console.log("Tbody Rows:", tbodyRows.length);

    var tbodyRowCount = 0;

    tbodyRows.each(function() {
        let cell = $(this).find('div#master_DefaultContent_rts_ts7046_s7048_f20653srvgrid_ctl00_ctl04_f20653\\:21738c');
        
        if (cell.length && cell.text().trim() === "Yes") {
            tbodyRowCount++;
        }
    });

    console.log("Tbody Row Count:", tbodyRowCount);

    if (consultCount) {						
        if (tbodyRowCount > 0 && consultCount != tbodyRowCount) {
            $("#master_btnApply").click();
        }
    }
});
