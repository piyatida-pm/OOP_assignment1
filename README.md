# Library Management System - Procedural Style

## Project Overview

This project is a **Library Management System (LMS)** implemented in **Python (Procedural + OOP Hybrid style)**.  
It allows managing **books, members, and borrowing/return transactions** in a simple console-based interface.

The main objective is to simulate how a basic library works —  
adding books, registering members, borrowing/returning books, and checking book availability — all using **Python lists, dictionaries, and classes**.

---

## Project Structure

LibraryManagementSystem/
│
├── library_system.py # Main Python script containing all classes and test function
├── README.md # Project documentation
└── (optional) requirements.txt # Not required (pure Python standard library)



---

## Design Overview

### 1. **Global Data Lists**

At the top of the script, three global lists are initialized:
```python
books = []
members = []
borrowed_books = []

These lists store the current state of the library:
books: all available books
members: registered members
borrowed_books: ongoing transactions of borrowed item
```

### 2. **Class Book**
Represents a book entity in the library.

**Attributes:**
```python
book_id (int) – Unique ID for each book
title (str) – Title of the book
author (str) – Author of the book
available_copies (int) – Number of copies currently available
```

**Methods:**
```python
1. __status__() → Returns a formatted string with book details
2. borrow_book(member_id, book_id) → Handles book borrowing logic
3. return_book(member_id, book_id) → Handles book return logic
- Note: Although borrow_book and return_book exist here, the main logic is centralized inside the Library class.
```

### 3. **Class Member**
Represents a library member.

**Attributes:**
```python
name (str) – Full name of the member
member_id (int) – Unique ID
email (str) – Member contact
borrowed_book (list) – List of borrowed book IDs
```

**Constants:**
```python
max_borrowed_limit = 3 → Maximum books each member can borrow
```
**Methods:**
```python
1. __status__() → Displays member details and number of borrowed books.
2. can_borrowed() → Returns True if the member can borrow more books
3. borr_book(book_id) → Adds a borrowed book to the member list
4. return_books(book_id) → Removes a returned book from the member list
```

### 4. **Class Library**

The core management class — handles operations between members and books.

**Attributes:**
```python
self.books (dict) – Dictionary for fast book lookups
self.members (dict) – Dictionary for fast member lookups
self.borrowed_transections (list) – Records of borrow/return events
```

**Methods:**
Method	Description
```python
- find_book(book_id) → Find a book by ID
- find_member(member_id) → Find a member by ID
- add_book(book_id, title, author, available_copies) → Add a new book to the library
- add_member(member_id, name, email) → Register a new member
- borrow_book(member_id, book_id) → Borrow a book if available
- return_book(member_id, book_id) → Return a borrowed book
- display_available_books() → Show all books that are still available
- display_member_books(member_id) → Show all books borrowed by a member
```

### 5. **Test Function test_library_system()**

A comprehensive test suite to demonstrate and validate all system functionalities step-by-step.

**Includes:**
```python
Adding books and members
Borrowing and returning books
Enforcing borrowing limits
Handling invalid or non-existent members/books
Displaying final library status
The test automatically prints formatted output for each scenario.
```
---
## How to Use

### 1. Run the Program
To run the demonstration script, open your terminal in the project directory and type:
```bash
python3 OOP_assi1.py
```

## Example

--- TEST 1: Adding Books ---
Book 'Python Crash Course' added successfully!
Book 'Clean Code' added successfully!
Book 'Design Patterns' added successfully!

--- TEST 2: Borrowing Books ---
Alice Smith borrowed 'Python Crash Course'

--- TEST 3: Returning Books ---
Alice Smith returned 'Python Crash Course'

--- TEST 4: Successful Borrowing ---
Alice Smith borrowed 'Python Crash Course'
Bob Jones borrowed 'Clean Code'
