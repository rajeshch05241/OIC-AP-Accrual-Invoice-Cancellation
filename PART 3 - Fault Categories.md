Continue from Prompt 1 and Prompt 2.

The OIC AP Accrual Invoice Cancellation integration is now designed.

Now focus ONLY on:

**FAULT HANDLING, ERROR HANDLING, RETRY, LOGGING, NOTIFICATIONS, AND REPROCESSING.**

Do not redesign the main business flow unless required.

## PART 1 — Fault Categories

Separate errors into:

### Business Errors

Examples:

- Invoice not found
- Invoice already cancelled
- Invoice not eligible
- Invoice already paid
- Invalid supplier
- Invalid Business Unit
- Invalid cancellation reason
- Duplicate request
- Missing mandatory data

### Technical Errors

Examples:

- SFTP unavailable
- SFTP authentication failure
- Fusion authentication failure
- HTTP 401
- HTTP 403
- HTTP 404
- HTTP 409
- HTTP 429
- HTTP 500
- HTTP 502
- HTTP 503
- Timeout
- Connection failure
- Mapping failure
- Stage File failure
- Invalid CSV
- Invalid XML/JSON

Explain how each should be handled.

## PART 2 — Scope Design

Review the scopes from Prompt 2.

For each scope explain whether it needs a fault handler.

Example:

Scope – Validation
Scope – Fusion Search
Scope – Cancellation
Scope – Status Update

Explain:

- Catch Fault
- Re-throw Fault
- Continue

## PART 3 — Scope Fault Handler

Give exact steps to configure a Scope Fault Handler in OIC.

Explain:

1. Open scope
2. Add Fault Handler
3. Add Catch Fault
4. Capture fault information
5. Assign error variables
6. Log error
7. Send notification
8. Decide Continue/Re-throw

## PART 4 — Global Fault Handler

Explain how to use the Global Fault Handler.

Show what should happen for unhandled integration errors.

Flow:

Unhandled Fault
↓
Global Fault Handler
↓
Capture Error
↓
Log
↓
Notification
↓
Re-throw

Explain when Global Fault Handler should be used instead of Scope Fault Handler.

## PART 5 — Error Variables

Create variables:

- vErrorCode
- vErrorMessage
- vFaultName
- vFaultDetails
- vFusionResponse
- vProcessingStatus
- vIntegrationInstanceId
- vInvoiceNumber
- vSourceReference

Explain how to populate each variable.

## PART 6 — Extract OIC Fault Details

Show valid OIC expressions/functions for extracting:

- Error code
- Error message
- Fault name
- Fault details
- HTTP status
- Fusion response

Do not invent unsupported OIC functions.

If exact expression depends on OIC version, explain that.

## PART 7 — Retry Logic

Create a retry strategy.

### Retry

- HTTP 429
- HTTP 500
- HTTP 502
- HTTP 503
- Timeout
- Temporary connection failure

### Do NOT Retry

- Invoice not found
- Invalid supplier
- Invalid BU
- Already cancelled
- Invoice not eligible
- Invalid cancellation reason
- Missing mandatory data

Explain:

- Retry count
- Retry interval
- Wait
- Re-submit
- Reprocessing

## PART 8 — ATP Error Logging

If ATP is part of the architecture, create an error logging table.

Include:

- Integration_Instance_ID
- Source_File_Name
- Record_Number
- Invoice_Number
- Supplier_Number
- Business_Unit
- Invoice_ID
- Processing_Status
- Error_Code
- Error_Message
- Fusion_Response
- Created_Date
- Updated_Date

Provide SQL CREATE TABLE.

Then explain exactly how OIC inserts the error.

## PART 9 — Success/Error Status

Define statuses:

- NEW
- PROCESSING
- SUCCESS
- ERROR
- RETRY
- ALREADY_PROCESSED
- NOT_ELIGIBLE

Explain when each status is assigned.

## PART 10 — Duplicate Processing

Design an idempotency mechanism.

Example:

Source Reference + Invoice Number + Cancellation Date

Before calling Fusion:

Check whether the cancellation was already successfully processed.

If YES:

Do not call Fusion again.

If NO:

Continue.

Explain how to implement this in OIC + ATP.

## PART 11 — Email Notification

Design email notifications.

### Error Email

Include:

- Integration name
- Integration instance
- File name
- Invoice number
- Supplier
- Business Unit
- Error code
- Error message
- Timestamp

### Batch Failure Email

Explain how to notify if the complete file fails.

## PART 12 — Partial Failure

This is important.

Suppose the file contains:

100 invoices

95 successful
5 failed

Explain how OIC should process this.

The integration should NOT unnecessarily stop all 100 records because of 1 failed record.

Show:

For Each
↓
Record Scope
↓
Try
↓
Success
OR
Catch Fault
↓
Log Error
↓
Continue Next Record

Explain whether sequential processing or parallel processing is safer.

## PART 13 — Complete Fault Architecture

Create an ASCII diagram:

Main Integration
↓
For Each
↓
Record Scope
├── Success
└── Fault Handler
      ├── Capture Error
      ├── Log Error
      ├── Notification
      └── Continue

Global Fault Handler
↓
Unhandled Error
↓
Log
↓
Notification
↓
Re-throw

## PART 14 — Error Matrix

Create a detailed table:

| Error | Type | Retry | OIC Action | Status | Notification |
|---|---|---|---|---|---|

Include at least 20 realistic errors.

## PART 15 — Reprocessing

Explain how a failed record can be reprocessed.

Cover:

- OIC Monitoring
- Resubmit
- Correct source data
- Retry
- ATP staging
- Duplicate prevention

## IMPORTANT

Use real Oracle OIC terminology.

Do not invent unsupported OIC features.

At the end create:

**"HANDOFF TO PROMPT 4"**

Summarize the final integration so Prompt 4 can create the testing, deployment, monitoring, and interview documentation.