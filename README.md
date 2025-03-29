<script src="https://code.jquery.com/jquery-3.7.1.min.js" integrity="sha256-/JqT3SQfawRcv/BIHPThkBvs0OEvtFFmqPF/lYI/Cxo=" crossorigin="anonymous"></script>

    <script>
        $(document).ready(function() {

            // --- Step 1a: Define Archer Field IDs for the Score Values ---
            // !!! CRITICAL: Replace placeholders with ACTUAL Archer Field IDs for scores !!!
            const archerFieldIdsForScores = {
                baselineInherentRisk: 401, // Field ID for the 'Baseline Inherent Risk' score
                businessProfile:      402, // Field ID for the 'Business Profile' score
                localRegulatory:      403, // Field ID for the 'Local Regulatory' score
                finalInherentRisk:    404, // Field ID for the 'Final Inherent Risk' score
                finalControlScore:    405  // Field ID for the 'Final Control Score'
            };

            // --- Step 1b: Define Archer Field IDs for the Badge Text ---
            // !!! CRITICAL: Replace placeholders with ACTUAL Archer Field IDs for badges !!!
            const archerFieldIdsForBadges = [
                // Calculated Row
                101, 102, 103,
                // Submitted Row
                201, 202, 203,
                // Approved Row
                301, 302, 303
            ]; // Ensure exactly 9 IDs in correct order

            // --- Step 2: Update the Scores Table ---
            console.log("Attempting to update scores table...");
            try {
                // Select the specific row containing the score cells.
                // This assumes the first table follows the h4 directly. Adjust if structure differs.
                // It targets the second <tr> within the first table's <tbody> (browsers often add tbody implicitly).
                const scoreRow = $('h4:contains("Calculated Risk Score") + table').find('tbody tr:nth-child(2)');

                if (scoreRow.length) {
                    // Helper function to get value and update a specific cell by its index (1-based)
                    const updateScoreCell = (cellIndex, fieldIdKey) => {
                        const cell = scoreRow.find(`td:nth-child(${cellIndex})`); // Find cell by index
                        const fieldId = archerFieldIdsForScores[fieldIdKey];      // Get corresponding Field ID

                        if (cell.length && fieldId) {
                            try {
                                // Get value from Archer
                                let value = ArcherTech.UI.GenericContent.GetInstant().getFieldValue(fieldId, false);
                                // Format for display (handle null/undefined, trim)
                                let textValue = (value !== null && typeof value !== 'undefined') ? String(value).trim() : '';
                                // Update cell content using jQuery's .text()
                                cell.text(textValue);
                                // console.log(`Set Score Cell ${cellIndex} (${fieldIdKey}) from Field ID ${fieldId} to: "${textValue}"`);
                            } catch (error) {
                                console.error(`Error getting/setting value for Score ${fieldIdKey} (Field ID: ${fieldId}):`, error);
                                cell.text('Error'); // Display 'Error' in the cell
                            }
                        } else if (!cell.length) {
                             console.warn(`Could not find score cell at index ${cellIndex} in the score row.`);
                        } else {
                             console.warn(`No Field ID defined for score key: ${fieldIdKey} in the configuration.`);
                        }
                    };

                    // Call the helper for each score cell, mapping index to the key in archerFieldIdsForScores
                    updateScoreCell(1, 'baselineInherentRisk'); // 1st cell
                    updateScoreCell(2, 'businessProfile');      // 2nd cell
                    updateScoreCell(3, 'localRegulatory');      // 3rd cell
                    updateScoreCell(4, 'finalInherentRisk');    // 4th cell
                    updateScoreCell(5, 'finalControlScore');    // 5th cell

                } else {
                    console.warn("Could not find the row containing scores in the 'Calculated Risk Score' table. Check table structure and selectors.");
                }
            } catch (error) {
                 console.error("A general error occurred while trying to update the scores table:", error);
            }

            // --- Step 3: Populate the 9 Badges using Archer function ---
            // (This logic remains the same as the previous response)
            console.log("Attempting to update badges...");
            const allBadges = document.querySelectorAll('.badge');
            if (allBadges.length >= 9) {
                for (let i = 0; i < 9; i++) {
                    const currentBadge = allBadges[i];
                    const fieldId = archerFieldIdsForBadges[i];
                    if (fieldId) {
                        try {
                            let fieldValue = ArcherTech.UI.GenericContent.GetInstant().getFieldValue(fieldId, false);
                            let badgeText = (fieldValue !== null && typeof fieldValue !== 'undefined') ? String(fieldValue).trim() : '';
                            currentBadge.textContent = badgeText;
                        } catch (error) {
                            console.error(`Error getting/setting value for Badge ${i + 1} (Field ID: ${fieldId}):`, error);
                            currentBadge.textContent = 'Error';
                        }
                    } else {
                        console.warn(`No Archer Field ID defined for Badge ${i + 1}.`);
                        currentBadge.textContent = '';
                    }
                }
            } else {
                console.warn(`Script expected at least 9 '.badge' elements, found only ${allBadges.length}.`);
            }

            // --- Step 4: Apply styling based on the FINAL text content of ALL badges ---
            // (This logic also remains the same)
            console.log("Applying styles to badges...");
            const badgesToStyle = document.querySelectorAll('.badge');
            const classMap = { /* ... class map definitions ... */ };
            const riskClasses = ['low', 'medium', 'high', 'very-high'];
            badgesToStyle.forEach(badge => {
                 const trimmedText = badge.textContent.trim();
                 riskClasses.forEach(cls => badge.classList.remove(cls)); // Cleanup first
                 if (trimmedText !== '' && trimmedText !== 'Error') {
                     const textContentLower = trimmedText.toLowerCase();
                     const cssClass = classMap[textContentLower];
                     if (cssClass) {
                         badge.classList.add(cssClass);
                     } else {
                         console.warn(`No style mapping found for badge text: "${trimmedText}"`);
                     }
                 }
            });

            console.log("Page processing complete.");
            // Other code that runs after DOM is ready...
        });
    </script>
