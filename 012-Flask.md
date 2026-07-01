##  Flask

**16. `Flask(__name__)`, `@app.route()`, `app.run()`?**
```python
from flask import Flask
app = Flask(__name__)   # creates the app instance
 
@app.route('/')          # defines a URL route
def home():
    return "Hello"
 
app.run()                # starts the development server
```
 
**17. How do you specify HTTP methods on a route?**
```python
@app.route('/users', methods=['GET', 'POST'])
def users():
    ...
```
 
**18. Difference between `request.args`, `request.json`, `request.form`?**
- `request.args` — query string parameters (`?key=value` in the URL).
- `request.json` — JSON data sent in the request body.
- `request.form` — form data sent (e.g. from an HTML form, `application/x-www-form-urlencoded`).
**19. What do `jsonify()` and `abort(404)` do?**
`jsonify()` converts a Python dict/list into a proper **JSON response** (with correct headers). `abort(404)` immediately stops the request and returns an **error response** with the given status code.
 
**20. What does `render_template()` do? What is Jinja2? `{{ }}`, `{% %}`?**
`render_template()` renders an **HTML template file** (usually from the `templates/` folder), optionally passing variables to it. **Jinja2** is Flask's templating engine. `{{ variable }}` outputs a value; `{% ... %}` is used for logic (loops, conditionals, blocks).
```html
<p>{{ name }}</p>
{% if user %}
  <p>Welcome</p>
{% endif %}
```
 
**21. What is template inheritance? `extends`, `block`?**
Template inheritance lets a "base" template define a common layout, and child templates **extend** it and override specific **blocks** (sections), avoiding repeated HTML code.
```html
<!-- base.html -->
<html><body>{% block content %}{% endblock %}</body></html>
 
<!-- child.html -->
{% extends "base.html" %}
{% block content %}<p>Page content</p>{% endblock %}
```
 
**22. How do you read data from JSON/CSV/SQLite and pass it to a template?**
Read/parse the data in the Flask route function (e.g. `json.load()`, `csv.reader()`, or a database query), then pass it as a variable into `render_template('page.html', data=my_data)`, and loop over it with `{% for item in data %}` in the template.
 
**23. How do you build a Flask REST API?**
Define routes that accept/return JSON instead of HTML, typically using `jsonify()` for responses and handling different HTTP methods (`GET`, `POST`, etc.) to perform CRUD operations on resources.
```python
@app.route('/api/users', methods=['GET'])
def get_users():
    return jsonify(users_list)
```
 
**24. What is a Blueprint used for?**
A **Blueprint** lets you organize a Flask app into modular, reusable groups of routes (e.g. separate files for `auth`, `users`, `products`), which are then registered on the main app — keeping large applications organized.
```python
from flask import Blueprint
users_bp = Blueprint('users', __name__)
 
@users_bp.route('/users')
def list_users():
    ...
 
app.register_blueprint(users_bp)
```
 
**25. What is the concept of token-based authentication (in Flask context)?**
The server issues a token (e.g. JWT) to the client after login. The client then sends this token with each subsequent request (usually in the `Authorization` header) to prove it's authenticated, instead of re-sending credentials or relying on server-side sessions.
 
**26. What is the concept of OpenAPI / Swagger?**
OpenAPI is a standard specification format for **describing REST APIs** (endpoints, parameters, responses, etc.) in a machine-readable way (usually YAML/JSON). **Swagger** is a set of tools built around OpenAPI that can generate interactive API documentation and testing interfaces from that specification.