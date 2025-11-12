# The MTV Architecture in Django

Django follows a pattern called **MTV**, which stands for:
- **Model**
- **Template**
- **View**

This is similar to the popular MVC (Model–View–Controller) pattern used in other frameworks, but Django’s naming is slightly different.

---

## 1. Model

The **Model** represents the data layer of your application.  
It defines the structure of your data and how it will be stored in the database.

For example, if you have a blog website, your model might describe a "Post" with fields like `title`, `author`, `content`, and `date_published`.

The model also provides tools to:
- Create and update records
- Retrieve data easily using Python
- Avoid writing raw SQL queries

Example (concept only):
> “Get all posts written by John and show them on the blog page.”

---

## 2. Template

The **Template** is the presentation layer.  
It controls how information is displayed to the user — usually using HTML.

Templates can include variables (data) and small bits of logic (for example, loops or conditionals) to display data dynamically.

Example:
> Display a list of blog posts inside an HTML page.

---

## 3. View

The **View** is the connection between the Model and the Template.  
It contains the main logic for what to show when a user visits a page.

A view decides:
- What data to get from the Model
- Which Template to use
- What response to send back to the user

Example:
> When someone visits `/blog/`, the view gets all posts from the model and tells the template to display them.

---

## How They Work Together

1. The **user** visits a page (sends a request).  
2. Django finds the matching **view**.  
3. The **view** gets or creates data from the **model**.  
4. The **view** sends the data to a **template**.  
5. The **template** formats the data into HTML.  
6. Django sends the HTML page as a **response** to the user.

---

## Summary

| Component | Purpose |
|------------|----------|
| Model | Manages the data and database |
| View | Controls what data to show and how |
| Template | Displays the data to the user |

The MTV pattern keeps each part of your web application separate and organized.  
It allows developers to change how data is displayed (template) without touching the database logic (model) or main logic (view).
