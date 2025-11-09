Data Entry Bot Workflow for Dynamic Webpage
----------------------------------------------------------------------

This workflow automates the process of entering data from an Excel file into a dynamic webpage where field positions, labels, and selectors change after every submission. The automation intelligently identifies fields based on their labels and relative positions, ensuring accurate data entry for all 50 Excel rows.

How To Create
---------------------------


Step 1: Objective

Objective: Automate dynamic webpage data entry for 50 Excel records.
Activity Used: Comment Activity (to describe workflow purpose).

Step 2: Input Data

The bot reads all records from an Excel file.
Activities Used:

Excel Application Scope (to open Excel file)

Read Range (to read entire Excel sheet into a DataTable variable named dtData)

Assign (to store Excel file path in a variable ExcelPath)

Step 3: Launch Browser

The bot opens the target form webpage.
Activities Used:

Open Browser (to launch the form webpage using URL variable)

Assign (to store URL of the webpage)

Output: Browser variable (used later to attach browser sessions)

Step 4: Loop Through Excel Records

The bot processes each record one by one.
Activities Used:

For Each Row in Data Table (to loop through all 50 Excel rows)

Write Line (to log current record being processed)

Step 5: Dynamic Field Detection

The bot intelligently identifies each field by using its nearby label or visual structure.
Activities Used:

Anchor Base (Find Element + Type Into)

Find Element (to locate label text like Name, Email, Address)

Type Into (to enter data relative to the found label)

If selectors are unpredictable, CV activities may be used:

CV Get Text (to read label)

CV Type Into (to enter value in corresponding field)

Step 6: Data Entry Process

For each field in the web form, the bot performs the following:
Activities Used:

Element Exists (to ensure field is present before typing)

Type Into (to type Name, Email, Address, etc.)

Log Message (to confirm each field typed successfully)

Delay (if needed for slow field loading)

Step 7: Form Submission

After completing all fields for one record, the bot submits the form.
Activities Used:

Click (to press the Submit button)

Wait Element Vanish (to wait for form reload or confirmation message)

Delay (optional, to allow form reset)

Step 8: Post-Submission Wait

The bot waits for the next form to appear after each submission.
Activities Used:

Element Exists (to verify new form loaded)

Delay (short pause before continuing next record)

Log Message (to confirm successful submission of one record)

Step 9: Error Handling

If any selector fails or field is missing, the bot continues with the next record.
Activities Used:

Try Catch (to handle runtime errors)

Log Message (to display the error details)

Continue (to skip current record and move to the next one)

Step 10: Loop for Next Record

After successful or failed submission, the bot automatically moves to the next Excel row.
Activities Used:

For Each Row (loop continues automatically)

Assign (update status variables or counters)

Write Line (to indicate next record started)

Step 11: Close Browser

After completing all 50 records, the bot closes the browser.
Activities Used:

Close Tab (to close webpage)

Kill Process (to ensure browser completely closed)

Log Message (to confirm process completed successfully)

Step 12: Key Variables

URL – Stores target webpage link
ExcelPath – Path of the Excel file
dtData – DataTable that holds all Excel data
row – Current row during loop
Browser – Variable used to maintain the browser session

Step 13: Workflow Highlights

Dynamic field detection using Anchor Base and CV activities
Excel-driven automation for 50 records
Error-tolerant, continues even if one record fails
Compatible with dynamic webpages where selectors change after each submission
Efficient use of retry, delay, and element wait mechanisms for stability

