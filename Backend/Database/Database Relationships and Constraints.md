# Database Relationships and Constraints

## Overview

Database relationships are heavily dependent on entities. Therefore, when inserting, updating, or deleting rows, it's essential to consider the order of these operations in relation to the tables involved. Proper management of relationships ensures data integrity throughout the database.

### Implementing Constraints for Data Integrity

Databases offer various mechanisms to implement constraints that maintain data integrity. For instance, PostgreSQL utilizes triggers to enforce these constraints. Additionally, SQL allows for the definition of foreign key constraints during table creation, which dictate actions to take when referenced data changes.

In this specific database, users will input human-readable data in a specific cascading order. This data primarily pertains to lab runners and opportunities, with related details cascading into tables that store this information. Consequently, foreign key constraints will link other tables to tuples in the lab runners or opportunities tables.

*Reference: [Why are constraints applied in the database rather than in the code?](https://dba.stackexchange.com/questions/39833/why-are-constraints-applied-in-the-database-rather-than-the-code)*

---

## Observations on the Opportunities Table

**Date: 10/31**

*Author: Duy "Sunny" Le*

I have identified a slight inconvenience with the database design. The opportunities table utilizes an autoincrement integer as a synthetic primary key (`opp_id`). When the client inserts new opportunities, they may not know this key, which complicates the relationships connecting opportunities to other data.

I am not fully acquainted with the implementation of inserting rows with autoincrement keys. It is possible that two identical opportunity rows (differing only by the `opp_id`) could be inserted inadvertently. This situation may lead to duplicate data, as two distinct keys could point to the same row. Issues arise only when the same key values correspond to different rows—please refer to materials on functional dependencies and primary keys for further clarification.

On a positive note, once inserted, opportunities will have a fixed `opp_id`, which could greatly enhance the application if it can query for an opportunity's `opp_id`. This key can then be utilized to retrieve all related data (as illustrated in the ER diagram).

---

## Database Constraints

Constraints serve as integrity rules for the database and can be categorized by their scope:

### Types of Constraints

- **Database Level:** Assertions
- **Table Level:** 
  - Primary Key
  - Foreign Key
  - Unique Constraint
  - Not Null Constraint
  - Check (attribute level or table level)

### Example of Constraint Implementation in PostgreSQL

```sql
DROP TABLE a;
DROP TABLE b;

CREATE TABLE a (
    id1 int PRIMARY KEY,
    id3 int
);

CREATE TABLE b (
    id2 int PRIMARY KEY,
    id1 int NOT NULL,
    FOREIGN KEY (id1) REFERENCES a(id1)
);

The order of data insertion is crucial, as foreign key constraints can prevent successful inserts. It's advisable to insert data into tables without foreign key constraints first.

Dropping Tables with Foreign Key Constraints
Attempting to drop a table that is referenced by another table via foreign key constraints will result in an error:

ERROR: cannot drop table a because other objects depend on it

To delete a table and all dependent tables, use:

DROP ... CASCADE

CREATE TABLE ABC (
    X int,
    Y int,
    PRIMARY KEY(X,Y)
);

CREATE TABLE DEF (
    Z int,
    W int,
    Q int,
    PRIMARY KEY(Z),
    FOREIGN KEY (Z,W)
        REFERENCES ABC(X,Y)
        ON DELETE CASCADE
        ON UPDATE SET NULL
);

In this example, DEF(Z,W) can be null (since there is no NOT NULL constraint). However, if values are provided, they must exist in DEF. If a tuple in ABC is deleted, all corresponding tuples in DEF will also be deleted (due to the CASCADE rule). If the primary key of a tuple in ABC is updated, the corresponding tuples in DEF will be set to null (SET NULL).

If no specific ON DELETE or ON UPDATE actions are defined, the default behavior is RESTRICT. In this case, an update or delete operation on ABC will fail if there are any referencing tuples in DEF.

All cascading and set null actions occur within the same transaction as the triggering insert, update, or delete operation.

