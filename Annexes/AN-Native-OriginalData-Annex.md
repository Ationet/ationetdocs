## Introduction

**Original Data** is a field of type `Dictonary<string, string>` meaning that every element in the collection has a **Key** and **Value**. The contents of this field represent another transaction (refered to as *Original*) that the current request is trying to reference. Used in **Refund**, **Void** and **Cancellation** transactions.

## Keys

| Key                       | Description                                 |
| ------------------------- | ------------------------------------------- |
| TransactionCode           | Original *Transaction*'s code               |
| LocalTransactionDate      | Original *Transaction*'s date               |
| LocalTransactionTime      | Original *Transaction*'s time               |
| AuthorizationCode         | Original *Transaction*'s authorization code |
| TransactionSequenceNumber | Original *Transaction*'s sequence number    |