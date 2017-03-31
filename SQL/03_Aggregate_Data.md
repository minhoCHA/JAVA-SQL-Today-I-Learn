# Aggregating Data

```sql

CREATE TABLE groceries (id INTEGER PRIMARY KEY, name TEXT, quantity INTEGER, aisle INTEGER);
INSERT INTO groceries VALUES (1, "Bananas", 4, 7);
INSERT INTO groceries VALUES(2, "Peanut Butter", 1, 2);
INSERT INTO groceries VALUES(3, "Dark Chocolate Bars", 2, 2);
INSERT INTO groceries VALUES(4, "Ice cream", 1, 12);
INSERT INTO groceries VALUES(5, "Cherries", 6, 2);
INSERT INTO groceries VALUES(6, "Chocolate syrup", 1, 4);

SELECT SUM(quantity) FROM groceries;
SELECT MAX(quantity) FROM groceries;
SELECT SUM(quantity) FROM groceries GROUP BY aisle;
SELECT aisle, SUM(quantity) FROM groceries GROUP BY aisle;
```
how did that actually work behind the scenes?

The SQL engine 
1. did the grouping of the rows based on aisle.
2. Then it summed up the quentity in each of those groups
3. And then, finally, it selected the first aisle value that it saw in each group

