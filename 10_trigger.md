## What is trigger and how to create a Trigger in SQL?

- Triggers in SQL are special stored procedures that are automatically executed when a specific event occurs in a database table.

- They provide a way to automate tasks and enforce data integrity rules without requiring manual intervention.

```
CREATE TRIGGER trigger_name
trigger_type ON table_name
FOR EACH ROW
BEGIN
    //body
END;
```

**Types of Triggers**

BEFORE INSERT: Triggered before a new row is inserted into a table
AFTER INSERT: Triggered after a new row is inserted into a table
BEFORE UPDATE: Triggered before a new row is updated into a table
AFTER UPDATE: Triggered after a new row is updated into a table
BEFORE DELETE: Triggered before a new row is deleted into a table
AFTER DELETE: Triggered after a new row is deleted into a table

**Events that Trigger Execution**

1. INSERT
2. UPDATE
3. DELETE

**Example**

DELIMITER //
CREATE trigger addlog
AFTER INSERT ON employee
FOR EACH ROW
BEGIN
INSERT INTO viewlog
(type, time, count)
VALUES
('insert', NOW(), 1);
END //
