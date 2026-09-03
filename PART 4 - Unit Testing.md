Continue from Prompts 1, 2, and 3.

The complete OIC AP Accrual Invoice Cancellation / Reversal integration has now been designed.

Now provide the final:

**TESTING + MONITORING + PERFORMANCE + DEPLOYMENT + PRODUCTION CHECKLIST + INTERVIEW EXPLANATION**

Do not redesign the integration.

## PART 1 — Unit Testing

Create detailed test cases.

At least 25 test cases.

Include:

1. Valid invoice cancellation
2. Invoice not found
3. Already cancelled
4. Invalid supplier
5. Invalid Business Unit
6. Missing invoice number
7. Missing cancellation reason
8. Invalid cancellation date
9. Paid invoice
10. Invoice not eligible
11. Duplicate cancellation
12. Duplicate file
13. Empty file
14. Invalid CSV
15. Invalid date format
16. Invalid amount
17. Invalid currency
18. SFTP failure
19. Fusion authentication failure
20. Fusion timeout
21. HTTP 429
22. HTTP 500
23. HTTP 503
24. Partial file failure
25. Successful complete file

For every test case provide:

- Test input
- Expected OIC behavior
- Expected Fusion behavior
- Expected status
- Expected notification
- Retry yes/no

## PART 2 — End-to-End Test

Show one complete successful example:

SFTP file
↓
OIC
↓
CSV
↓
Validation
↓
Fusion Search
↓
Invoice ID
↓
Cancellation
↓
Fusion response
↓
SUCCESS
↓
Archive file

Use a realistic sample invoice.

## PART 3 — Negative Test

Show one complete failure example:

CSV
↓
OIC
↓
Invoice Search
↓
Invoice Not Found
↓
Business Error
↓
Fault Handler
↓
Error Log
↓
ERROR
↓
Next Record

## PART 4 — Partial Success

Example:

100 records

95 SUCCESS
5 ERROR

Explain exactly how OIC handles this.

## PART 5 — Monitoring

Explain OIC monitoring.

Cover:

- Integration instances
- Tracking fields
- Business identifiers
- Errors
- Activity Stream
- Fault details
- Resubmit
- Purging

Recommended tracking fields:

- Invoice Number
- Supplier Number
- Business Unit
- Source Reference
- File Name

## PART 6 — Performance

Explain:

- Large CSV files
- Read Entire File vs Segments
- For Each
- Sequential vs Parallel
- Fusion API throttling
- Retry
- Database commits
- Batch size
- API limits

Recommend the safest production configuration.

## PART 7 — Security

Provide production security checklist:

- SFTP credentials
- SSH keys
- Fusion credentials
- OAuth
- Certificates
- OIC security
- Password protection
- Avoid sensitive data in logs
- Credential rotation

## PART 8 — Deployment

Create:

DEV
↓
TEST
↓
SIT
↓
UAT
↓
PROD

Explain what needs to be migrated:

- Connections
- Lookups
- Integration
- Packages
- Certificates
- Security credentials
- ATP objects

Explain environment-specific configuration.

## PART 9 — Production Checklist

Create a checklist for:

### Connections
### Integration
### Fusion
### SFTP
### Database
### Lookups
### Security
### Fault Handling
### Notifications
### Monitoring
### Performance
### Scheduling
### Reprocessing

## PART 10 — Support Runbook

Create troubleshooting procedures for:

### File not picked up
### File processing failed
### Invoice not found
### Fusion API failure
### Authentication failure
### Timeout
### Duplicate invoice
### Partial failure
### Database logging failure

For each provide:

Problem
↓
How to check
↓
Likely cause
↓
Resolution
↓
Reprocessing approach

## PART 11 — Final Architecture

Create the final architecture diagram containing:

SFTP
↓
OIC Scheduler
↓
Read File
↓
Stage File
↓
For Each
↓
Validation
↓
Fusion Invoice Search
↓
Invoice Validation
↓
Fusion Cancellation
↓
Success/Error
↓
ATP Logging
↓
Notification
↓
Archive

Include Scope Fault Handler and Global Fault Handler.

## PART 12 — Interview Explanation

Give me three versions.

### 1-Minute Explanation

Explain the project professionally in about 1 minute.

### 3-Minute Explanation

Explain:

- Requirement
- Source
- OIC architecture
- Adapters
- Mapping
- Fusion API
- Validation
- Fault handling
- Logging
- Monitoring

### 5-Minute Deep-Dive

Explain:

- Integration pattern
- SFTP
- Stage File
- For Each
- Variables
- Fusion invoice search
- Invoice validation
- Cancellation
- Scopes
- Fault handlers
- Retry
- ATP logging
- Idempotency
- Partial failure
- Monitoring

## PART 13 — Interview Questions

Create at least 20 interview questions and answers specifically based on this integration.

Examples:

1. Why did you use Scheduled Orchestration?
2. Why did you use SFTP?
3. Why did you use Stage File?
4. Why For Each?
5. Why sequential processing?
6. How do you identify the invoice?
7. How do you validate invoice status?
8. How do you cancel the invoice?
9. Which Fusion API did you use?
10. How do you handle 401?
11. How do you handle 429?
12. How do you handle timeout?
13. How do you handle partial failures?
14. How do you prevent duplicate cancellation?
15. How do you implement fault handlers?
16. Difference between Scope Fault Handler and Global Fault Handler?
17. When do you rethrow an error?
18. How do you log errors?
19. How do you monitor production?
20. How do you reprocess failed records?

Give strong, practical interview answers.

## FINAL REQUIREMENT

At the end provide a single:

**COMPLETE OIC IMPLEMENTATION CHECKLIST**

with every item from:

1. Connections
2. Lookups
3. Integration creation
4. SFTP
5. Stage File
6. For Each
7. Variables
8. Validation
9. Fusion Search
10. Invoice Status Validation
11. Cancellation
12. Mapping
13. Success handling
14. Scope Fault Handler
15. Global Fault Handler
16. Retry
17. ATP Logging
18. Notifications
19. Tracking
20. Testing
21. Deployment
22. Monitoring
23. Reprocessing
24. Production Support

This should be the final project implementation document that an OIC developer can use as a reference.