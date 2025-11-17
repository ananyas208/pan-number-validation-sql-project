

## Project Summary
A SQL-based data validation project where I designed an end-to-end workflow to clean, validate, and report on PAN (Permanent Account Number) data.  
This project demonstrates analytical thinking, use of regex and procedural SQL, and the ability to translate data quality challenges into structured, automated SQL solutions.

---

## Overview
This project showcases how **SQL can be used for real-world data cleaning, pattern validation, and reporting**.  
As an analyst, I approached the task of validating and cleaning a dataset of **PAN (Permanent Account Number)** records — a common data quality issue in financial or government datasets — by designing an end-to-end validation workflow entirely within SQL.  

The goal was to ensure every PAN follows the correct format, remove inconsistencies, and provide a transparent view of data quality through SQL-based functions, regex, and summary reports.

---

## Objective
To build a **data validation framework** in SQL that can:  
1. Identify missing, duplicate, or malformed PAN entries.  
2. Standardize data formatting (case, spacing, duplicates).  
3. Validate the structural integrity of each PAN using **regular expressions and pattern logic**.  
4. Categorize records as **Valid** or **Invalid** and summarize overall data health.

---

##  Problem-Solving Approach  

| Step | Description | SQL Techniques Used |
|------|--------------|--------------------|
| **1. Data Profiling** | Checked for missing, null, and duplicate PANs. | `COUNT`, `GROUP BY`, `HAVING`, `IS NULL` |
| **2. Data Cleaning** | Removed spaces, standardized letter casing, removed duplicates. | `TRIM`, `UPPER`, `DISTINCT` |
| **3. Structural Validation** | Ensured PAN follows the pattern `AAAAA9999A`. | Regex: `^[A-Z]{5}[0-9]{4}[A-Z]$` |
| **4. Logical Validation** | Created SQL functions to detect repeated or sequential characters. | Custom `PL/pgSQL` functions |
| **5. Reporting** | Summarized valid vs. invalid records. | `CTE`, `CASE WHEN`, aggregate logic |

---

##  Tools & Technologies
- **Language:** SQL  
- **Database:** PostgreSQL (PL/pgSQL for custom logic)  
- **Dataset:** `PAN Number Validation Dataset.csv`  
- **IDE:** pgAdmin / DBeaver  

---

## Key Analytical Functions  

#  `fn_check_adjacent_characters(p_str text)`  
Detects repeated adjacent characters (e.g., `AAZPK...` → invalid).  
Helps prevent artificially generated PANs.

# `fn_check_sequential_char(p_str text)`  
Identifies sequential characters (e.g., `ABCDE` or `12345`) to flag potentially fake patterns.

### Regex Validation  
Used pattern:  
```
^[A-Z]{5}[0-9]{4}[A-Z]$
```
Ensures the PAN follows the official structural rule — 5 letters, 4 digits, and 1 letter.

---

## Summary Report  
At the end of the process, a summary table highlights the **data quality metrics**.

| Metric | Description |
|--------|--------------|
| `total_processed_records` | Total PAN entries received |
| `total_valid_pans` | Number of valid PANs after checks |
| `total_invalid_pans` | Records failing regex or logical validation |
| `total_missing_pans` | Null or incomplete PAN records |

---

## Sample Output


---

## Analytical Learnings  
- Strengthened understanding of **data validation pipelines** using SQL.  
- Applied **regex and procedural SQL** to create robust validation rules.  
- Improved data profiling and reporting skills.  
- Learned how to design logic-based checks (sequences, adjacency) that mirror **real-world fraud detection** or **data integrity use cases**.  

---

## Repository Structure  
```
pan-number-validation-sql-project/
│
├── README.md
├── script.sql
├── Project_scripts.txt
├── PAN Number Validation Dataset.csv
└── Output_Screenshots/
```
