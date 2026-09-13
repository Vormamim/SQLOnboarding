# Lesson 2 - Create Tables and Add Data

## Time

**75 minutes**

## Learning goals

By the end of this lesson, students should be able to:

- create a table
- choose simple column types
- insert rows into a table
- save changes with `commit()`

## Why this matters

Creating tables and adding records is the first step toward building any real database-backed project.

## Key theory

- A table needs a clear structure before data can be stored.
- `CREATE TABLE` defines the table and its columns.
- `INSERT INTO` adds new rows.
- `commit()` saves changes to the database file.

## Glossary

- **schema**: the structure of a database
- **primary key**: a unique identifier for each row
- **INTEGER**: whole number data
- **TEXT**: text data
- **INSERT**: SQL command used to add data
- **commit**: save database changes permanently

## Explicit code

Create a file named `lesson2_create_table.py`:

```python
import sqlite3

connection = sqlite3.connect("school.db")
cursor = connection.cursor()

cursor.execute("""
CREATE TABLE IF NOT EXISTS students (
    id INTEGER PRIMARY KEY,
    name TEXT NOT NULL,
    year_group INTEGER
)
""")

cursor.execute("DELETE FROM students")

cursor.execute("INSERT INTO students (name, year_group) VALUES (?, ?)", ("Ava", 10))
cursor.execute("INSERT INTO students (name, year_group) VALUES (?, ?)", ("Leo", 11))

connection.commit()
connection.close()
```

## Student activity

1. Create the script shown above.
2. Run it in VS Code.
3. Change one student name and run it again.
4. Discuss why `IF NOT EXISTS` is useful.
5. Identify which column is the primary key.

## Stretch challenge

- Add a third student.
- Add a new `TEXT` column called `favorite_subject`.

## Exit check

- Why do we use `commit()`?
- What does `PRIMARY KEY` mean?
