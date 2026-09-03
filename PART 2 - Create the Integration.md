Continue from the architecture and design you created in Prompt 1.

Now I want to actually BUILD the integration in Oracle Integration Cloud.

Do not redesign the architecture unless something in Prompt 1 is technically incorrect.

Focus only on the **complete OIC development/build steps**.

Integration:

**AP Accrual Invoice Cancellation / Reversal**

Source:

**SFTP CSV → OIC → Oracle Fusion Cloud Payables**

## PART 1 — Create the Integration

Give exact OIC console steps:

1. Create integration
2. Select integration pattern
3. Integration name
4. Identifier
5. Version
6. Description
7. Schedule configuration

Explain what to select on each screen.

## PART 2 — Configure SFTP

Explain step-by-step:

1. Add SFTP/FTP trigger or invoke
2. Select operation
3. Configure file name pattern
4. Configure directory
5. Download/read file
6. Archive file
7. Error file directory
8. Duplicate file handling

Use an example:

AP_ACCRUAL_CANCEL_YYYYMMDD.csv

## PART 3 — Stage File

Explain exactly how to configure Stage File.

Show:

- Read File
- Read Entire File vs Read in Segments
- CSV schema
- Delimiter
- Header
- Record structure
- Encoding
- File reference

Explain which option is recommended.

## PART 4 — For Each

Determine whether For Each is required.

If yes, explain exactly:

- Which collection to select
- Repeating element
- Current record
- Variables
- Scope placement

Show the flow:

For Each Record
↓
Validate
↓
Search Invoice
↓
Validate Invoice
↓
Cancel Invoice
↓
Update Status

## PART 5 — Variables

Create a complete variable list.

Include variables such as:

- vInvoiceNumber
- vSupplierNumber
- vBusinessUnit
- vInvoiceId
- vInvoiceStatus
- vCancellationDate
- vCancellationReason
- vProcessingStatus
- vErrorCode
- vErrorMessage
- vSourceReference
- vCorrelationId

For each variable provide:

- Name
- Data type
- Initial value
- Where it is assigned
- Where it is used

## PART 6 — Source Validation

Create exact OIC validation logic.

Validate:

1. Invoice Number
2. Supplier Number
3. Business Unit
4. Cancellation Date
5. Cancellation Reason
6. Amount
7. Currency
8. Source Reference

Explain which OIC action to use:

- If
- Switch
- Assign
- Scope

Provide valid OIC/XPath expressions wherever possible.

## PART 7 — Search Fusion Invoice

Give the detailed configuration for finding the invoice in Fusion.

Explain:

- Adapter
- Operation
- Endpoint
- HTTP method if REST
- Query parameters
- Required headers
- Authentication
- Request
- Response

Use:

Invoice Number + Supplier + Business Unit

if appropriate.

Show how to extract:

**InvoiceId**

from the Fusion response.

## PART 8 — Validate Fusion Invoice

After finding the invoice, validate:

- Invoice exists
- Invoice number matches
- Supplier matches
- Business Unit matches
- Invoice status
- Payment status
- Cancellation status
- Eligibility for cancellation

Create the exact Switch/If decision logic.

Example:

Invoice not found
→ ERROR

Already cancelled
→ ALREADY_PROCESSED

Not eligible
→ ERROR

Eligible
→ Continue

## PART 9 — Cancel Invoice

Explain the exact configuration of the Fusion cancellation operation.

Identify whether to use:

**Oracle ERP Cloud Adapter**

or

**REST Adapter**

Show:

- Operation
- Endpoint
- HTTP method if REST
- Request payload
- Required parameters
- Invoice ID
- Cancellation date
- Cancellation reason
- Response

IMPORTANT:

Do not invent fields or API operations.

If the operation depends on Fusion release, clearly identify what must be verified.

## PART 10 — Source-to-Fusion Mapping

Create a mapping table:

| Source Field | OIC Variable | Fusion Target | Transformation |
|---|---|---|---|

Include:

Invoice Number
Supplier Number
Business Unit
Cancellation Date
Cancellation Reason
Amount
Currency
Invoice ID

Explain every important mapping.

## PART 11 — Date Handling

Explain:

Source date
→ OIC transformation
→ Fusion date

Cover:

- YYYY-MM-DD
- DD-MM-YYYY
- Date vs DateTime
- Null date
- Invalid date
- Time zone

Provide valid OIC expressions.

## PART 12 — Lookup

Identify whether lookups are required.

Possible lookups:

- Cancellation Reason
- Business Unit
- Source System
- Status

Show:

- Lookup creation
- Lookup values
- lookupValue() usage
- Default handling

## PART 13 — Success Processing

After successful cancellation:

1. Capture Fusion response
2. Extract response values
3. Set SUCCESS
4. Store processing information
5. Update staging table if used
6. Continue to next record

## PART 14 — Complete OIC Flow

Finally show the complete OIC designer flow:

Schedule
↓
SFTP
↓
Stage File
↓
Read CSV
↓
For Each
↓
Scope
↓
Validation
↓
Fusion Search
↓
Status Validation
↓
Cancellation
↓
Response
↓
Success

For every action tell me exactly what OIC action/adapter I should drag onto the canvas.

## IMPORTANT

Do not cover detailed fault handling yet.

At the end create:

**"HANDOFF TO PROMPT 3"**

Summarize the exact scopes, variables, adapters, and actions that Prompt 3 must add fault handling to.