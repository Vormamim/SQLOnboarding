# Lesson 1 - Setup and First Database Connection

## Time

**60 minutes**

## Learning goals

By the end of this lesson, students should be able to:

- explain what a database is
- explain what SQLite is
- open a project in VS Code
- run a Python file from the terminal
- connect to a SQLite database with Python

## Why this matters

Students need a clear mental model of how Python, SQLite, files, and VS Code fit together before they can write useful database programs.

## Key theory

- A **database** stores information in an organized way.
- **SQLite** is a lightweight database engine that stores data in a single file.
- **Python** can talk to SQLite using the built-in `sqlite3` module.
- A **connection** lets Python open and work with a database file.

## Glossary

- **database**: an organized collection of data
- **table**: a grid of rows and columns
- **row**: one record in a table
- **column**: one type of information in a table
- **SQLite**: a file-based SQL database engine
- **connection**: the active link between Python and the database

## Explicit code

Create a file named `lesson1_connect.py`:

```python
import sqlite3

connection = sqlite3.connect("school.db")
print("Database connected!")
connection.close()
print("Database closed!")
```

Run it in the VS Code terminal:

```bash
python lesson1_connect.py
```

## Student activity

1. Open VS Code.
2. Create a folder for the project.
3. Create `lesson1_connect.py`.
4. Type the code exactly as shown.
5. Run the file from the terminal.
6. Confirm that a `school.db` file appears in the folder.

## Stretch challenge

- Change the database file name to `library.db`.
- Add one more `print()` line explaining what the script is doing.

## Exit check

- What is the difference between Python and SQLite?
- What file was created when the script ran?
