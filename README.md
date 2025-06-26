# BulkTriggerContact (Salesforce Apex Trigger)

This is a Salesforce Apex Trigger that runs **after update** on the Contact object.

---

## What It Does:
- Checks if the **Email** field has changed during an update.
- If the email is updated, it logs the change in the `Description` field:
  > "Email was changed from old@example.com to new@example.com"
- Supports **bulk-safe operations** by using a separate list for DML.

---

## Trigger Type:
- `after update`

---

## Use Case:
- Track/audit changes to Contact email addresses.
- Helpful for teams that want visibility into user communication changes.

---

## Best Practices Followed:
- Handles **bulk updates**
- Avoids DML inside loops
- Uses `Trigger.oldMap` to compare previous values

---

## How to Test (Manually)

### 1. Insert Test Contacts:
```apex
List<Contact> testContacts = new List<Contact>();
for(Integer i = 1; i <= 3; i++) {
    testContacts.add(new Contact(LastName = 'Test' + i, Email = 'test' + i + '@example.com'));
}
insert testContacts;

List<Contact> contactsToUpdate = [SELECT Id, Email FROM Contact WHERE LastName LIKE 'Test%'];
for(Contact con : contactsToUpdate) {
    con.Email = 'updated_' + con.Email;
}
update contactsToUpdate;
