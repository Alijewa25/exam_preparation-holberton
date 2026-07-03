# Additional Quiz Bank — Linux, Git, Error Handling, OOP Advanced, REST API, Flask, Extra Topics

Same format as `015-holberton-quiz-bank.md`: multiple-choice style, correct answer(s) marked with ✅ and briefly explained.

---

## 🐧 Linux Shell

**Q0.** What does `pwd` print?
- The list of files in the folder
- ✅ **The full path of the current directory**
- The username
- The last command run

**Q1.** What is the difference between `ls` and `ls -a`?
- `ls -a` sorts alphabetically, `ls` doesn't
- ✅ **`ls -a` shows hidden files (starting with `.`) too, `ls` doesn't**
- They are identical
- `ls -a` only works on directories

**Q2.** What does `cd ..` do?
- Goes to the home directory
- ✅ **Moves to the parent directory**
- Creates a new directory
- Closes the terminal

**Q3.** What happens if you run `touch newfile.txt` and `newfile.txt` already exists?
- It throws an error
- It deletes the file
- ✅ **It updates the file's last-modified timestamp, content unchanged**
- It duplicates the file

**Q4.** What is the difference between `cp file1 file2` and `mv file1 file2`?
- They behave identically
- ✅ **`cp` creates a copy (original stays); `mv` moves/renames it (original is gone)**
- `mv` only works on directories
- `cp` deletes the source file

**Q5.** What does `rm -rf folder/` do?
- Renames the folder
- Lists folder contents recursively
- ✅ **Forcefully and recursively deletes the folder and everything inside it, no confirmation**
- Compresses the folder

**Q6.** What is the difference between `mkdir new_folder` and `mkdir -p a/b/c`?
- No difference
- ✅ **`mkdir -p` creates all missing parent directories in the path; plain `mkdir` fails if parents don't exist**
- `-p` makes the folder private
- `-p` deletes existing folders first

**Q7.** Which path is **absolute**?
- `../docs/file.txt`
- `docs/file.txt`
- ✅ **`/home/user/docs/file.txt`**
- `./file.txt`

**Q8.** What does `less file.txt` let you do that `cat file.txt` doesn't?
- Edit the file
- ✅ **Scroll through a large file page by page instead of dumping it all at once**
- Delete lines
- Compress the file

**Q9.** What is the difference between `rmdir` and `rm -r`?
- They are the same command
- ✅ **`rmdir` only removes an empty directory; `rm -r` removes a directory and its contents, even if not empty**
- `rmdir` is for files only
- `rm -r` cannot delete folders

---

## 🔧 Git / GitHub

**Q0.** What does `git init` do?
- Uploads a repo to GitHub
- ✅ **Initializes a new, empty Git repository in the current folder**
- Deletes the `.git` folder
- Clones a repository

**Q1.** What is the correct order of the basic Git workflow?
- commit → add → push
- ✅ **add → commit → push**
- push → add → commit
- commit → push → add

**Q2.** What does `git status` show?
- The commit history
- ✅ **Which files are staged, modified, or untracked in the working directory**
- The list of branches
- The remote URL

**Q3.** What is the difference between `git push` and `git pull`?
- They do the same thing
- ✅ **`push` sends local commits to the remote; `pull` fetches and merges remote changes into local**
- `pull` only works once
- `push` deletes remote branches

**Q4.** What does `git clone <url>` do?
- Creates a new empty repo
- ✅ **Downloads a full copy of an existing remote repository, including its history**
- Merges two repos
- Deletes a repo

**Q5.** What is the difference between `git checkout -b feature` and `git checkout feature`?
- They are identical
- ✅ **`-b` creates a new branch called `feature` and switches to it; without `-b`, it switches to an existing branch**
- `-b` deletes the branch
- `-b` only works on `main`

**Q6.** What is the key difference between `git reset` and `git revert`?
- They are the same
- ✅ **`reset` rewrites history by removing commits; `revert` adds a new commit that undoes changes, preserving history**
- `revert` deletes all commits
- `reset` is safe on shared branches, `revert` is not

**Q7.** What is the purpose of a `.gitignore` file?
- Stores commit messages
- ✅ **Lists files/folders that Git should NOT track (e.g. `node_modules/`, `.env`)**
- Backs up deleted files
- Lists all branches

**Q8.** Why is a Personal Access Token (PAT) used instead of a password for GitHub HTTPS operations?
- PATs are shorter
- ✅ **GitHub no longer accepts account passwords for Git operations; PATs are scoped, revocable, and more secure**
- PATs never expire
- Passwords are faster

**Q9.** What causes a merge conflict?
- Running `git status` too often
- ✅ **Two branches modify the same lines of a file (or one deletes a file the other edited), and Git can't auto-merge them**
- Forgetting `git init`
- Using `git clone` twice

---

## 🐍 Error Handling & Documentation

**Q0.** What does this print?
```python
try:
    x = 1 / 0
except ZeroDivisionError:
    print("Error caught")
```
- Nothing
- A crash/traceback
- ✅ **Error caught**
- `1/0`

**Q1.** What does `finally` guarantee?
- It only runs if an exception occurs
- It only runs if no exception occurs
- ✅ **It always runs, whether an exception occurred or not**
- It stops the program

**Q2.** What does `raise ValueError("bad input")` do?
- Catches an existing error
- ✅ **Manually triggers a `ValueError` exception with the given message**
- Prints "bad input" and continues
- Does nothing without a `try` block

**Q3.** What kind of error does `int("abc")` raise?
- `TypeError`
- ✅ **`ValueError`**
- `KeyError`
- `ZeroDivisionError`

**Q4.** What kind of error does `{"a": 1}["b"]` raise?
- `ValueError`
- `IndexError`
- ✅ **`KeyError`**
- `TypeError`

**Q5.** What is a docstring used for?
- To comment out code
- ✅ **To document what a module, class, or function does, placed right after its definition as a string literal**
- To define variables
- To improve performance

**Q6.** Where is a **module-level** docstring placed?
- Inside every function
- ✅ **At the very top of the `.py` file, before any code**
- At the bottom of the file
- Inside `__init__`

**Q7.** What does this code print?
```python
def divide(a, b):
    try:
        return a / b
    except ZeroDivisionError:
        return None
    finally:
        print("Done")

print(divide(10, 0))
```
- `10/0`
- `None` then `Done`
- ✅ **Done** then **None** — `finally` runs before the function's return value is actually printed
- Error/crash

---

## 🧱 OOP — Advanced

**Q0.** What does `super().__init__()` do inside a subclass's `__init__`?
- Deletes the parent's attributes
- ✅ **Calls the parent class's constructor, typically to initialize inherited attributes**
- Creates a new class
- Overrides all parent methods

**Q1.** What happens if a subclass calls `self.attribute` before calling `super().__init__()`, where `attribute` is set in the parent's `__init__`?
- It works fine
- ✅ **It raises an `AttributeError`, since the parent's `__init__` hasn't run yet to set that attribute**
- It uses a default value
- It automatically calls `super()` first

**Q2.** What is method overriding?
- Deleting a parent method
- ✅ **A subclass defining a method with the same name as one in its parent, replacing that behavior**
- Calling a method twice
- Renaming a method

**Q3.** What is multiple inheritance?
- A class with multiple `__init__` methods
- ✅ **A class inheriting from more than one parent class at the same time, e.g. `class C(A, B)`**
- Inheriting the same class twice
- Not allowed in Python

**Q4.** What does `isinstance(obj, MyClass)` check?
- If `MyClass` is a subclass of `obj`
- ✅ **If `obj` is an instance of `MyClass` (or one of its subclasses)**
- If `obj` has no class
- If `MyClass` exists

**Q5.** What does `@abstractmethod` (from the `abc` module) enforce?
- The method runs automatically
- ✅ **Any concrete subclass MUST implement this method, or it can't be instantiated**
- The method can't be overridden
- The method is private

**Q6.** What happens when you try to instantiate a class that inherits from `ABC` and has an unimplemented `@abstractmethod`?
- It works normally
- ✅ **It raises a `TypeError`, since abstract classes with unimplemented abstract methods can't be instantiated**
- It silently skips the method
- It auto-implements the method

**Q7.** What is "duck typing" in Python?
- Checking an object's exact class before using it
- ✅ **Caring about whether an object has the right behavior/methods, not its exact type ("if it walks like a duck...")**
- A type of inheritance
- A built-in Python function

**Q8.** What is a mixin class typically used for?
- As the main base class of an app
- ✅ **Adding small, reusable pieces of functionality to other classes via multiple inheritance, without standing alone**
- Storing constants only
- Replacing `__init__`

**Q9.** In a custom iterator class, what does `__next__` do when there are no more items?
- Returns `None`
- Returns `0`
- ✅ **Raises `StopIteration`**
- Restarts the loop automatically

---

## 🌐 REST API

**Q0.** What does REST stand for?
- Rapid External State Transfer
- ✅ **Representational State Transfer**
- Remote Endpoint Service Transfer
- Resource State Transaction

**Q1.** What does "stateless" mean in REST?
- The server stores session data between requests
- ✅ **Each request must contain all information needed; the server keeps no client session state**
- The client has no state
- APIs can't have variables

**Q2.** Which HTTP method is used to **create** a new resource?
- GET
- ✅ **POST**
- DELETE
- PATCH

**Q3.** Which HTTP method fully **replaces** an existing resource?
- PATCH
- ✅ **PUT**
- GET
- POST

**Q4.** What does HTTP status code `404` mean?
- Server error
- Unauthorized
- ✅ **Resource not found**
- Bad request

**Q5.** What does HTTP status code `201` mean?
- OK, generic success
- ✅ **Created — a new resource was successfully created**
- Forbidden
- Server error

**Q6.** Which HTTP methods are considered **idempotent**?
- Only POST
- ✅ **GET, PUT, DELETE**
- Only DELETE
- None of them

**Q7.** What is the difference between a query parameter and a path parameter?
- They are the same thing
- ✅ **Path params identify a specific resource in the URL path (`/users/5`); query params filter/modify the request after `?` (`/users?age=25`)**
- Query params are required, path params are optional
- Path params only work with POST

---

## 🍶 Flask

**Q0.** What does `app = Flask(__name__)` do?
- Starts the server immediately
- ✅ **Creates a Flask application instance**
- Defines a route
- Connects to a database

**Q1.** What does `@app.route('/users')` do?
- Creates a database table called users
- ✅ **Maps the URL `/users` to the function defined right below the decorator**
- Deletes the `/users` endpoint
- Imports the users module

**Q2.** What is the difference between `request.args` and `request.json`?
- No difference
- ✅ **`request.args` reads query string parameters; `request.json` reads JSON data from the request body**
- `request.json` is for GET only
- `request.args` is for POST only

**Q3.** What does `jsonify({"name": "Ali"})` return?
- A Python dictionary
- ✅ **A proper Flask JSON HTTP response with correct headers**
- A string
- An HTML page

**Q4.** What does `abort(404)` do inside a Flask route?
- Logs a warning and continues
- ✅ **Immediately stops the request and returns a 404 Not Found response**
- Restarts the server
- Deletes the resource

**Q5.** What does `render_template('page.html', name=name)` do?
- Returns raw HTML as a string with no processing
- ✅ **Renders the Jinja2 template `page.html`, injecting the `name` variable into it**
- Creates a new HTML file
- Redirects to another route

**Q6.** In Jinja2, what is the difference between `{{ variable }}` and `{% if condition %}`?
- No difference
- ✅ **`{{ }}` outputs a value; `{% %}` is used for logic like loops and conditionals**
- `{% %}` outputs a value; `{{ }}` is for logic
- Both are Python syntax, not Jinja2

**Q7.** What does template inheritance (`{% extends %}` / `{% block %}`) achieve?
- Makes templates load faster
- ✅ **Lets child templates reuse a shared base layout and override specific sections, avoiding repeated HTML**
- Combines Python files
- Encrypts templates

**Q8.** What is the purpose of a Flask Blueprint?
- To style the app with CSS
- ✅ **To organize a large app into modular, reusable groups of routes registered on the main app**
- To connect to a database
- To handle authentication only

**Q9.** In `methods=['GET', 'POST']` on a route, what does this control?
- The route's URL
- ✅ **Which HTTP methods the route will accept/respond to**
- The response format
- The template used

---

## 🗄️ Extra Topics — DB Design, Backend, CORS, Git

**Q0.** What is the purpose of a Foreign Key?
- Uniquely identifies a row in its own table
- ✅ **References the Primary Key of another table, creating a relationship between tables**
- Encrypts a column
- Speeds up all queries automatically

**Q1.** What problem does normalization primarily solve?
- Slow queries
- ✅ **Data redundancy and update anomalies, by organizing tables to minimize duplicate data**
- Server crashes
- Login failures

**Q2.** How is a many-to-many relationship typically implemented?
- With a single shared column
- ✅ **Using a junction/join table holding foreign keys to both related tables**
- It's not possible in SQL
- With a trigger

**Q3.** What is the purpose of a database index?
- To store backups
- ✅ **To speed up data retrieval/search on a column, at the cost of extra storage and slower writes**
- To encrypt data
- To enforce foreign keys

**Q4.** What is a virtual environment (`venv`) used for in Python projects?
- To run code faster
- ✅ **To isolate a project's installed packages from the system-wide Python, avoiding dependency conflicts**
- To connect to GitHub
- To compile Python to C

**Q5.** Why should a `.env` file be added to `.gitignore`?
- It slows down commits
- ✅ **It typically contains secrets (API keys, passwords) that shouldn't be committed to version control**
- It's a binary file
- Git can't read `.env` files

**Q6.** What is CORS?
- A Python library for testing
- ✅ **A browser security mechanism controlling whether a page from one origin can request resources from another origin**
- A type of SQL join
- A Git branching strategy

**Q7.** What does the `Content-Type` HTTP header indicate?
- The size of the request
- ✅ **The format of the request/response body (e.g. `application/json`)**
- The sender's IP address
- The HTTP method used

**Q8.** What does `git stash` do?
- Permanently deletes uncommitted changes
- ✅ **Temporarily saves uncommitted changes so you can switch branches with a clean working directory**
- Commits changes automatically
- Pushes changes to remote

**Q9.** What is the main tradeoff of `git rebase` compared to `git merge`?
- Rebase is always slower
- ✅ **Rebase creates a cleaner, linear history but rewrites commits, making it risky on shared/public branches**
- Merge deletes history
- There is no difference

---

*Total: 65 additional multiple-choice questions with answers — Linux, Git, Error Handling, OOP Advanced, REST API, Flask, and Extra Topics.*