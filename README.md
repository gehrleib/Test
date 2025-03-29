<style>
    /* Container for the summary content */
    .summary-container {
        padding: 20px;
        border-radius: 8px;
        max-width: 800px;
        margin: 20px auto;
    }

    /* h4 header style */
    .summary-header {
        font-size: 1.1rem;
        font-weight: bold;
        margin-bottom: 10px;
        color: #333; /* Darker text for headers */
    }

    /* Table styles */
    .summary-table {
        width: 100%;
        border-collapse: collapse;
        font-size: 0.9rem;
        background-color: rgb(255, 255, 255); /* White background for table */
    }

    .summary-table th, .summary-table td {
        border: 1px solid #ddd; /* Light gray border */
        padding: 8px;
        text-align: center;
    }

    .summary-table th {
        background: rgb(232, 232, 232); /* Header background color */
        font-weight: bold;
        color: #333; /* Darker text for readability */
    }

    /* Highlight class */
    .highlight {
        background-color: rgb(242, 242, 242); /* Subtle highlight color */
        font-weight: bold;
    }

    /* Formula note styles */
    .formula-note {
        font-size: 0.9rem;
        color: #333; /* Darker text */
        text-align: left;
        margin-top: 20px;
        padding: 15px;
        background-color: rgb(250, 250, 250); /* Light gray background */
        border: 1px solid #ddd; /* Light border */
        border-radius: 8px;
        margin-bottom: 20px;
        font-family: 'Open Sans', sans-serif;
        max-width: 80%;
        margin-left: auto;
        margin-right: auto;
    }

    /* Formula layout with two columns */
    .formula-layout {
        display: grid;
        grid-template-columns: 2fr 0.5fr 3fr; /* Add an extra space for the = sign */
        gap: 10px;
        align-items: center;
    }

    .formula-left {
        font-weight: bold;
        text-align: left;
        white-space: nowrap; /* Prevent line break */
        color: #333; /* Darker text */
    }

    .formula-equal {
        font-size: 1.2rem; /* Increase size of = */
        text-align: center;
        font-weight: bold;
        color: #333; /* Darker text */
    }

    .formula-right {
        font-family: 'Consolas', 'Courier New', monospace; /* Use monospace font */
        text-align: left;
        word-wrap: break-word;
        color: #333; /* Darker text */
    }

    /* Badge styles */
    .badge {
        padding: 5px 10px;
        border-radius: 5px;
        font-weight: bold;
        display: inline-block;
        width: 80px;
    }
    .low { background-color: #4CAF50; color: white; }      /* Green */
    .medium { background-color: #FFC107; color: black; }   /* Yellow */
    .high { background-color: #FF9800; color: white; }     /* Orange */
    .very-high { background-color: #F44336; color: white; } /* Red */
</style>

<div class="summary-container">
    <h4 class="summary-header">Calculated Risk Score</h4>
    <table class="summary-table">
        <tr>
            <th>Baseline Inherent Risk</th>
            <th>Business Profile</th>
            <th>Local Regulatory</th>
            <th>Final Inherent Risk</th>
            <th>Final Control Score</th>
        </tr>
        <tr>
            <td class="highlight">65</td>
            <td class="highlight">6</td>
            <td class="highlight">35</td>
            <td>65</td>
            <td>95</td>
        </tr>
    </table>

    <!-- Styled formula note with two columns: left and right -->
    <div class="formula-note">
        <div class="formula-layout">
            <div class="formula-left">
                <strong>Final Inherent Risk Score</strong>
            </div>
            <div class="formula-equal">
                =
            </div>
            <div class="formula-right">
                <span>max(Baseline Inherent Risk, (Business Profile + Local Regulatory))</span>
            </div>
        </div>
    </div>

    <h4 class="summary-header mt-3">Risk Ratings</h4>
    <table class="summary-table">
        <tr>
            <th>Type</th>
            <th>Inherent Risk</th>
            <th>Control Rating</th>
            <th>Residual Risk</th>
        </tr>
        <tr>
            <td><strong>Calculated</strong></td>
            <td><span class="badge"></span></td>
            <td><span class="badge"></span></td>
            <td><span class="badge"></span></td>
        </tr>
        <tr>
            <td><strong>Submitted</strong></td>
            <td><span class="badge"></span></td>
            <td><span class="badge"></span></td>
            <td><span class="badge"></span></td>
        </tr>
        <tr>
            <td><strong>Approved</strong></td>
            <td><span class="badge"></span></td>
            <td><span class="badge"></span></td>
            <td><span class="badge"></span></td>
        </tr>
    </table>
</div>

<script>
    $(document).ready(function() {

        // --- Step 1: Define mapping from Badge Index (0-8) to Archer Field ID ---
        // !!! CRITICAL: Replace placeholder numbers below with your ACTUAL Archer Field IDs !!!
        const archerFieldIdsForBadges = [
            // --- Calculated Row ---
            101, // Field ID for Badge 1 (Calculated Inherent Risk Text)
            102, // Field ID for Badge 2 (Calculated Control Rating Text)
            103, // Field ID for Badge 3 (Calculated Residual Risk Text)
            // --- Submitted Row ---
            201, // Field ID for Badge 4 (Submitted Inherent Risk Text)
            202, // Field ID for Badge 5 (Submitted Control Rating Text)
            203, // Field ID for Badge 6 (Submitted Residual Risk Text)
            // --- Approved Row ---
            301, // Field ID for Badge 7 (Approved Inherent Risk Text)
            302, // Field ID for Badge 8 (Approved Control Rating Text)
            303  // Field ID for Badge 9 (Approved Residual Risk Text)
        ];
        // Ensure this array has exactly 9 Field IDs in the correct order.

        // --- Step 2: Select all badge elements ---
        // This assumes the 9 target badges are the first 9 elements with class '.badge'
        // found in the HTML source order. Adjust selector if needed.
        const allBadges = document.querySelectorAll('.badge');

        // --- Step 3: Populate the first 9 badges using Archer function ---
        if (allBadges.length >= 9) {
            console.log("Found at least 9 badges. Attempting to populate from Archer fields...");
            for (let i = 0; i < 9; i++) { // Loop through the first 9 badges (index 0 to 8)
                const currentBadge = allBadges[i];
                const fieldId = archerFieldIdsForBadges[i];

                if (fieldId) { // Make sure a Field ID is defined for this position
                    try {
                        // Call the Archer function to get the value for the specific field ID
                        let fieldValue = ArcherTech.UI.GenericContent.GetInstant().getFieldValue(fieldId, false);

                        // Convert the result to a string and trim whitespace.
                        // Handle null/undefined values explicitly.
                        let badgeText = '';
                        if (fieldValue !== null && typeof fieldValue !== 'undefined') {
                            badgeText = String(fieldValue).trim();
                        }

                        // Set the text content of the current badge
                        currentBadge.textContent = badgeText;
                        // console.log(`Set Badge ${i + 1} (Field ID: ${fieldId}) text to: "${badgeText}"`);

                    } catch (error) {
                        console.error(`Error getting/setting value for Badge ${i + 1} (Field ID: ${fieldId}):`, error);
                        // Decide what to show in the badge on error (e.g., empty or 'Error')
                        currentBadge.textContent = 'Error';
                    }
                } else {
                    console.warn(`No Archer Field ID defined for Badge ${i + 1} in the configuration.`);
                    currentBadge.textContent = ''; // Set to empty if no ID is mapped
                }
            }
        } else {
            console.warn(`Script expected at least 9 '.badge' elements to populate, but found only ${allBadges.length}. Check your HTML structure or the selector.`);
        }

        // --- Step 4: Apply styling based on the FINAL text content of ALL badges ---
        // This code runs AFTER the badges have been populated above.
        console.log("Applying styles to badges...");
        const badgesToStyle = document.querySelectorAll('.badge'); // Use the potentially updated badges
        const classMap = {
            'low': 'low',
            'medium': 'medium',
            'high': 'high',
            'very high': 'very-high',
            'adequate': 'low',
            'partially adequate': 'medium',
            'inadequate': 'very-high'
        };
        const riskClasses = ['low', 'medium', 'high', 'very-high'];

        badgesToStyle.forEach(badge => {
            const trimmedText = badge.textContent.trim();

            // Clean up old classes first (recommended)
            riskClasses.forEach(cls => badge.classList.remove(cls));

            if (trimmedText !== '' && trimmedText !== 'Error') { // Don't style 'Error' text, perhaps
                const textContentLower = trimmedText.toLowerCase();
                const cssClass = classMap[textContentLower];
                if (cssClass) {
                    badge.classList.add(cssClass);
                } else {
                    console.warn(`No style mapping found for badge text: "${trimmedText}"`);
                }
            }
        });
    });
</script>
