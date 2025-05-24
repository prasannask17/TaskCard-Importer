# TaskCard-Importer

Step-by-Step Workflow Breakdown:
📥 Received
  The client uploads a Task Card Excel file (<<FileName>>.xlsx) into the system.

🔍 Sanity Check
  Validates the structure of the Excel file (template format).
  On Success: File moves to the ToBeProcessed stage as TBP Excel.
  On Failure: Logged as Error Excel (<<YYYYMMDD_HHMMSS>>_Error.xlsx).

📊 Pre-validation
  Validates data content:
  Data type checks
  Field length verification
  Mandatory fields presence
  On Success: File proceeds to Application Validation.
  On Failure: Generates a Failure Excel (<<YYYYMMDD_HHMMSS>>_Fail.xlsx) containing rows with validation issues.

🔐 Application Validation
  Validates domain-specific business rules:
  Task Card XML file and schema validation
  Existence checks for Task Card, Part Number, and Owner
  On Success: File proceeds to Task Card Creation.
  On Failure: Also results in a Failure Excel.

📝 Task Card Creation
  Validated entries are processed and task cards are generated.

📤 Final Output
  A Success Excel (<<FileName>>_Succ.xlsx) is created and saved with a timestamp.

🔁 Reprocessing Failed Data
  The Failure Excel can be corrected by the client and resubmitted in the next processing cycle, entering again from the Received stage.
