# BulkTriggerContact

This is a Salesforce Apex Trigger that runs after the Contact object is updated.

### What it does:
- Checks if the Email field has changed.
- If changed, it updates the `Description` field to log the old and new email.
- Follows best practices for bulk-safe triggers using separate DML list.

### Type: `after update` trigger  
### Use case: Audit email changes for Contacts

Tested and verified via Anonymous Apex in Developer Console.
