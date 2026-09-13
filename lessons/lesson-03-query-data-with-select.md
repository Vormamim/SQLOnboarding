# Lesson 3 - Query Data with SELECT

## Time

**75 minutes**

## Learning goals

By the end of this lesson, students should be able to:

- use `SELECT` to read data
- use `fetchall()` to get query results in Python
- loop through rows and print results clearly

## Why this matters

Students usually care most about seeing stored information again, so reading data is where SQL starts to feel practical and rewarding.

## Key theory

- `SELECT` reads data from a table.
- `*` means "all columns."
- Python can store query results in lists of rows.
- Clean output helps students understand what the data means.

## Glossary

- **SELECT**: SQL command used to read data
- **query**: a request for data
- **result**: the data returned by a query
- **cursor**: object used to run SQL commands
- **fetchall**: gets all returned rows from a query

## Explicit code

Create a file named `lesson3_select.py`:

```python
import sqlite3

connection = sqlite3.connect("school.db")
cursor = connection.cursor()

cursor.execute("SELECT id, name, year_group FROM students")
rows = cursor.fetchall()

for row in rows:
    print(row)

connection.close()
```

## Student activity

1. Run the script and read the output.
2. Change the query to `SELECT name FROM students`.
3. Add one more student in the database and run the script again.
4. Count how many rows are returned.

## Stretch challenge

- Format the output as:

```python
for student_id, name, year_group in rows:
    print(f"{name} is in year {year_group}.")
```

## Exit check

- What is the job of `SELECT`?
- What type of value does `fetchall()` return?
