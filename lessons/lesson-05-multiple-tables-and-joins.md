# Lesson 5 - Work with Multiple Tables

## Time

**75 minutes**

## Learning goals

By the end of this lesson, students should be able to:

- explain why databases often use more than one table
- create a second table
- connect related tables with IDs
- use a simple `JOIN`

## Why this matters

Using more than one table introduces the relational thinking that makes databases powerful and different from simple spreadsheets.

## Key theory

- Real databases often split data into related tables.
- A **foreign key** links one table to another.
- A `JOIN` combines matching information from more than one table.
- Using multiple tables reduces repeated data.

## Glossary

- **foreign key**: a column that points to a row in another table
- **relationship**: how two tables connect
- **JOIN**: SQL operation that combines data from multiple tables
- **duplicate data**: repeated information stored in many places

## Explicit code

Create a file named `lesson5_join.py`:

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

cursor.execute("""
CREATE TABLE IF NOT EXISTS courses (
    id INTEGER PRIMARY KEY,
    course_name TEXT NOT NULL,
    student_id INTEGER
)
""")

cursor.execute("DELETE FROM students")
cursor.execute("DELETE FROM courses")

cursor.execute(
    "INSERT INTO students (name, year_group) VALUES (?, ?)",
    ("Ava", 10)
)
ava_id = cursor.lastrowid

cursor.execute(
    "INSERT INTO students (name, year_group) VALUES (?, ?)",
    ("Leo", 11)
)
leo_id = cursor.lastrowid

cursor.execute(
    "INSERT INTO courses (course_name, student_id) VALUES (?, ?)",
    ("Science Club", ava_id)
)
cursor.execute(
    "INSERT INTO courses (course_name, student_id) VALUES (?, ?)",
    ("Math Team", leo_id)
)

cursor.execute("""
SELECT students.name, courses.course_name
FROM students
JOIN courses ON students.id = courses.student_id
""")

rows = cursor.fetchall()
for row in rows:
    print(row)

connection.commit()
connection.close()
```

## Student activity

1. Create both tables in one script.
2. Add one or two course records.
3. Run the `JOIN` query.
4. Explain which columns are used to connect the tables.

## Stretch challenge

- Add a second course for a different student.
- Ask students to predict the joined output before running the script.

## Exit check

- Why do we use more than one table?
- What is the purpose of `JOIN`?
