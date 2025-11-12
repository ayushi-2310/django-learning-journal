# **models.md**

# Understanding Django Models

## Overview

A **model** in Django is a Python class that defines the structure of your data.
It tells Django what kind of information you want to store and how it should be organized in the database.

In simple words, **a model is like a blueprint for a database table**.
Each model class represents a table, and each attribute (variable) inside that class represents a column in that table.

---

## Why Django Uses Models

Normally, when you use a database, you have to write SQL queries like this:

```sql
SELECT * FROM students WHERE age > 18;
```

But Django makes this easier.
You can do the same thing using simple Python code:

```python
students = Student.objects.filter(age__gt=18)
```

So instead of writing complex SQL, Django lets you talk to the database using **Python classes and methods** — this is called the **ORM (Object-Relational Mapper)**.

---

## What is the ORM

ORM stands for **Object Relational Mapper**.
It acts as a bridge between your Python code and the database.

* You write Python classes (models).
* Django converts them into database tables automatically.
* You can then create, read, update, and delete data using Python instead of SQL.

This means you don’t have to worry about database details — Django takes care of it.

---

## How a Model is Defined

A Django model is defined as a class that inherits from `models.Model`.

Example (conceptually):

```python
from django.db import models

class Student(models.Model):
    name = models.CharField(max_length=100)
    age = models.IntegerField()
    grade = models.CharField(max_length=10)
```

Here’s what this means:

* `Student` is the model name (it will become a table in the database).
* `name`, `age`, and `grade` are the fields (columns).
* `models.CharField()` and `models.IntegerField()` define the type of data that each field can store.

---

## Common Field Types

| Field Type      | Description               | Example                                                |
| --------------- | ------------------------- | ------------------------------------------------------ |
| `CharField`     | Text data (short strings) | `name = models.CharField(max_length=100)`              |
| `TextField`     | Long text                 | `description = models.TextField()`                     |
| `IntegerField`  | Whole numbers             | `age = models.IntegerField()`                          |
| `FloatField`    | Decimal numbers           | `price = models.FloatField()`                          |
| `BooleanField`  | True or False values      | `is_active = models.BooleanField(default=True)`        |
| `DateField`     | Date values               | `date_of_birth = models.DateField()`                   |
| `DateTimeField` | Date and time             | `created_at = models.DateTimeField(auto_now_add=True)` |
| `EmailField`    | Email addresses           | `email = models.EmailField()`                          |

---

## How Django Uses Models

When you create models, Django can automatically:

1. **Create database tables** for them (using migrations).
2. **Add data** to those tables.
3. **Fetch and display data** when needed.
4. **Update or delete records** easily.

Conceptually:

* You define models → Django makes tables.
* You write Python code → Django runs SQL for you.

---

## Example: Storing Book Information

Let’s imagine you want to store books in a library system.
You can define a model like this:

```python
class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.CharField(max_length=100)
    published_year = models.IntegerField()
    available = models.BooleanField(default=True)
```

This single class tells Django everything about how to store books — no SQL needed.
Django will create a table with columns: `id`, `title`, `author`, `published_year`, and `available`.

---

## Relationships Between Models

In real applications, models often connect to each other. Django supports three main relationships:

| Relationship Type | Meaning                                          | Example                                            |
| ----------------- | ------------------------------------------------ | -------------------------------------------------- |
| **One-to-One**    | One object is linked to exactly one other object | A `User` has one `Profile`                         |
| **One-to-Many**   | One object can be linked to many others          | One `Author` can have many `Books`                 |
| **Many-to-Many**  | Many objects can be linked to many others        | A `Book` can have many `Categories` and vice versa |

Example (conceptually):

```python
class Author(models.Model):
    name = models.CharField(max_length=100)

class Book(models.Model):
    title = models.CharField(max_length=200)
    author = models.ForeignKey(Author, on_delete=models.CASCADE)
```

Here, each book is linked to one author, but an author can have many books.

---

## Key Takeaways

* A **Model** is a Python class that defines a database table.
* Django’s **ORM** lets you interact with the database using Python instead of SQL.
* Each **field** in a model represents a column in the database.
* Models can be linked to each other using **relationships** (one-to-one, one-to-many, many-to-many).
* Django handles the database automatically — you only define models once, and it does the rest.


