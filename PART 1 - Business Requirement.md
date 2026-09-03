You are an expert Oracle Integration Cloud (OIC) Consultant and Oracle Fusion Cloud Financials Consultant.

I need to design a real-world OIC integration for:

**AP Accrual Invoice Cancellation / Reversal in Oracle Fusion Cloud Payables**

I want to build this integration step-by-step in Oracle Integration Cloud.

For now, DO NOT explain fault handling, testing, or interview preparation. Focus only on the **business process, architecture, integration pattern, connections, adapters, and overall design**.

## Business Requirement

The source system provides AP Accrual Invoice Cancellation records in a CSV file.

The CSV file is placed on an SFTP server.

OIC must:

1. Pick up the CSV file from SFTP.
2. Read and parse the CSV file.
3. Process each invoice cancellation record.
4. Validate the source data.
5. Find the corresponding AP invoice in Oracle Fusion Payables.
6. Validate that the invoice can be cancelled.
7. Cancel/reverse the invoice using the correct Oracle Fusion API or ERP Cloud operation.
8. Capture the Fusion response.
9. Mark the record as successful or failed.
10. Continue processing other records where appropriate.

## Source CSV Fields

Assume the source contains:

- Invoice Number
- Supplier Number
- Supplier Name
- Business Unit
- Invoice Date
- Cancellation Date
- Cancellation Reason
- Amount
- Currency
- Source System
- Source Reference

## PART 1 — Explain the Business Process

Explain clearly:

1. What is an AP Accrual Invoice?
2. What is invoice cancellation?
3. What is invoice reversal?
4. Why would an accrual invoice be cancelled?
5. What happens to accounting when an invoice is cancelled?
6. What validations are normally required before cancellation?
7. Which invoice statuses may prevent cancellation?

Keep this specific to Oracle Fusion Cloud Payables.

## PART 2 — Select the OIC Integration Pattern

Recommend the appropriate OIC integration pattern.

The source is an SFTP CSV file and processing is expected to be scheduled.

Evaluate:

- Scheduled Orchestration
- App Driven Orchestration
- REST Trigger

Select the recommended pattern and explain why.

## PART 3 — Complete Architecture

Create a detailed end-to-end architecture:

SFTP
↓
OIC Scheduled Integration
↓
Read File
↓
Stage File
↓
Read CSV
↓
For Each Record
↓
Validation
↓
Fusion Invoice Search
↓
Invoice Eligibility Validation
↓
Fusion Invoice Cancellation
↓
Response Processing
↓
Success / Failure Status

Improve the architecture if necessary.

Also provide an ASCII architecture diagram.

## PART 4 — ALL REQUIRED OIC ADAPTERS

Identify the exact adapters required.

Consider:

1. FTP Adapter / SFTP
2. Oracle ERP Cloud Adapter
3. REST Adapter
4. ATP Database Adapter
5. Email Adapter

Clearly separate:

### Mandatory adapters

and

### Optional adapters

Do NOT add unnecessary adapters.

For every adapter explain:

- Adapter name
- Trigger or Invoke
- Purpose
- Direction
- When it is used
- Important configuration
- Authentication
- Endpoint type

## PART 5 — CONNECTIONS

Explain the OIC connections that need to be created before building the integration.

For example:

### SFTP Connection

Explain:
- Connection type
- Security
- Authentication
- Host
- Port
- Directory
- File handling

### Oracle Fusion Connection

Explain:
- Oracle ERP Cloud Adapter
- Authentication
- Security policy
- Fusion URL
- Required credentials/roles
- Whether REST or ERP Cloud business operation should be used

### ATP Connection

Only include this if you recommend ATP for staging/error logging.

Explain why it is useful.

### Email Connection

Only include this if required for notifications.

## PART 6 — Fusion API / Operation

Identify the correct Oracle Fusion Cloud Payables API or ERP Cloud Adapter operation needed to:

1. Search/find an AP invoice.
2. Retrieve the invoice ID.
3. Validate invoice status.
4. Cancel the invoice.

IMPORTANT:

Do NOT invent API endpoints, operation names, fields, or payloads.

If the exact operation depends on the Oracle Fusion release, clearly state that.

Explain whether we should use:

- Oracle ERP Cloud Adapter business operation
OR
- REST Adapter calling Fusion REST API

Recommend the preferred approach for this project.

## PART 7 — High-Level OIC Flow

Give me the final recommended OIC flow in this format:

1. Schedule
2. SFTP
3. Stage File
4. Read CSV
5. For Each
6. Validation
7. Fusion Invoice Search
8. Invoice Status Validation
9. Fusion Cancellation
10. Response Handling
11. Status Update

For every step explain:

**What it does**
**Why it is required**
**What OIC action/adapter is used**

## IMPORTANT

This is Prompt 1 of a multi-step implementation.

Do not move into detailed fault handlers, error handling, test cases, or interview preparation yet.

At the end, provide a section called:

**"HANDOFF TO PROMPT 2"**

Summarize the architecture and decisions that Prompt 2 should continue from.

The result must be practical and suitable for a real Oracle OIC project, not just a theoretical explanation.