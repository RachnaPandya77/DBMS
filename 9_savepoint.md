## What is save Point? How to create a save Point write a Query?

- Savepoints in SQL are temporary markers within a transaction that allow you to roll back the transaction to a specific point if needed.
- They provide more granular control over transactions compared to simply rolling back the entire transaction.

**To create a savepoint, you use the SAVEPOINT statement**

<BR> 
The syntax is as follows :

_SAVEPOINT label_name;_

**Why Use Savepoints?**

- Fine-grained control
- Error handling
- Testing
