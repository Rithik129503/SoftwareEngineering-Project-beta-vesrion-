# Library Management System

A command-line application in Python (SQLite) to manage books, members, issuing and returning, with automatic due dates and fines.

## 1. Requirements
**Functional:** add books and members; search by title/author; issue a book (14-day loan); return a book; calculate fine (Rs 2/day late); list issued books.
**Non-functional:** simple CLI, data persists in `library.db`, input validated, no third-party libraries.
**Rules:** max 3 books per member; no issue if no copies are free; a member cannot hold two copies of one book.

## 2. Design (3-layer architecture)
- `main.py` - presentation layer (menu/CLI)
- `library/services.py` - business logic (`Library` class, `LibraryError`)
- `library/database.py` - data layer (SQLite schema)

**Tables:** `books(id, title, author, copies)`, `members(id, name, email)`, `issues(id, book_id, member_id, issue_date, due_date, return_date, fine)`.
Relationships: one member has many issues; one book has many issues.

## 3. How to run
```
python main.py
python -m unittest discover tests -v
```

## 4. Testing
Unit tests in `tests/test_library.py` cover due date, availability, borrow limit, fines, duplicate email and search.

## 5. Possible extensions
Login for librarian/member roles, book reservation, GUI (Tkinter), export reports to CSV.
