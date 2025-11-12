# How Django Works

To understand Django better, let’s look at how it handles a simple request.

---

## Step 1: A User Sends a Request

When a user types a website address into their browser (for example, `example.com/home`), the browser sends a **request** to the server.

This request is like asking, “Hey, please show me the Home page.”

---

## Step 2: Django Receives the Request

Django receives this request and starts looking for a **URL pattern** that matches `/home`.

Django keeps a list of all the URL patterns in a file called `urls.py`.  
If it finds one that matches, it sends the request to the correct **view** function.

---

## Step 3: The View Decides What to Do

A **view** is a Python function that decides what information to send back to the user.

- If the view needs to show some data from the database, it will ask the **model** for that data.
- If it only needs to display a page, it will choose the correct **template** (HTML file).

---

## Step 4: The Template Renders the Response

The **template** takes the data (if any) and turns it into an HTML page that looks nice in the browser.

Finally, Django sends this page back to the user as a **response**.

---

## Step 5: The User Sees the Page

The user’s browser receives the HTML response and displays it.  
From the user’s point of view, it looks like a normal webpage.

---

## Example (Conceptual)

Let’s imagine a user visits `example.com/books`.

1. Django finds that the `/books` URL is connected to a view called `show_books`.
2. The `show_books` view asks the model for all the books stored in the database.
3. The model returns that data.
4. The view gives the data to the template.
5. The template creates an HTML page showing the list of books.
6. Django sends that page to the user.

This process happens very quickly, often in less than a second.

---

## Key Point

Django separates each step (URL, View, Model, Template) clearly.  
This makes it easier to understand, maintain, and expand your website later.
