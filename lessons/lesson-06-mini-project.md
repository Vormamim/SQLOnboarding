# Lesson 6 - Build a Mini Project in Python

## Time

**60 minutes**

## Learning goals

By the end of this lesson, students should be able to:

- combine previous skills in one script
- create a simple menu-driven Python program
- store and display records from a SQLite database

## Why this matters

The mini project gives students a chance to combine isolated skills into one complete workflow they can explain and extend.

## Key theory

- Small projects help students connect isolated skills into one workflow.
- Breaking work into steps makes database programs easier to understand.
- Reusing simple SQL commands is enough to build a useful beginner app.

## Glossary

- **CRUD**: create, read, update, delete
- **menu**: a set of choices shown to the user
- **workflow**: the order of steps in a process

## Explicit code

Create a file named `lesson6_project.py`:

```python
import sqlite3

connection = sqlite3.connect("school.db")
cursor = connection.cursor()

cursor.execute("""
CREATE TABLE IF NOT EXISTS books (
    id INTEGER PRIMARY KEY,
    title TEXT NOT NULL,
    author TEXT NOT NULL
)
""")

cursor.execute("INSERT INTO books (title, author) VALUES (?, ?)", ("Holes", "Louis Sachar"))
cursor.execute("SELECT title, author FROM books ORDER BY title")

for title, author in cursor.fetchall():
    print(f"{title} by {author}")

connection.commit()
connection.close()
```

## Student activity

1. Build the script exactly as shown.
2. Add two more books.
3. Run the script and confirm all books print in order.
4. Ask students to explain which parts are Python and which parts are SQL.

## Stretch challenge

- Turn the script into a simple menu with options such as:
  - add a book
  - show all books
  - exit

## Exit check

- Which skills from earlier lessons were reused here?
- What would you add next to improve the app?
