# Code Analysis — Exam Prep (Multiple Choice)

Test-format version: code snippet + options, correct answer marked ✅ with a short explanation. Matches the real exam format (multiple choice only).

---

## 🐍 Python — Predict the Output

**Q0.**
```python
x = 5
y = x
x = 10
print(y)
```
- 10
- ✅ **5**
- Error
- None

Explanation: `y = x` copies the integer **value** at that moment. Reassigning `x` afterward doesn't affect `y`.

---

**Q1.**
```python
a = [1, 2, 3]
b = a
b.append(4)
print(a)
```
- [1, 2, 3]
- ✅ **[1, 2, 3, 4]**
- Error
- [4]

Explanation: `b = a` makes `b` reference the **same list object**. Modifying `b` also changes `a`.

---

**Q2.**
```python
def add_item(item, lst=[]):
    lst.append(item)
    return lst

print(add_item(1))
print(add_item(2))
```
- [1] then [2]
- ✅ **[1] then [1, 2]**
- [1] then [1]
- Error on second call

Explanation: Mutable default argument bug — the default list is created **once** at function definition and reused across calls.

---

**Q3.**
```python
for i in range(3):
    if i == 1:
        continue
    print(i)
```
- 0 1 2
- ✅ **0 2**
- 0 1
- 1 2

Explanation: `continue` skips `print(i)` only when `i == 1`, moving to the next iteration.

---

**Q4.**
```python
print(1 == 1.0)
print(1 is 1.0)
```
- True then True
- False then False
- ✅ **True then False**
- False then True

Explanation: `==` compares value (equal numerically). `is` compares identity — `int` and `float` are different object types.

---

**Q5.**
```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
finally:
    print("Done")
```
- Cannot divide by zero
- Done
- ✅ **Cannot divide by zero, then Done**
- Error crash, nothing printed

Explanation: `except` catches the error and prints its message; `finally` always runs afterward.

---

**Q6.**
```python
d = {"a": 1, "b": 2}
print(d.get("c", 0))
print(d["c"])
```
- 0 then 0
- ✅ **0 then raises KeyError**
- None then None
- Error on both lines

Explanation: `.get()` with a default never raises; direct `dict[key]` access raises `KeyError` if the key is missing.

---

## 🧱 OOP — Read & Explain

**Q7.**
```python
class Animal:
    def __init__(self, name):
        self.name = name
    def speak(self):
        return f"{self.name} makes a sound"

class Dog(Animal):
    def speak(self):
        return f"{self.name} barks"

a = Animal("Generic")
d = Dog("Rex")
print(a.speak())
print(d.speak())
```
- Generic makes a sound / Generic makes a sound
- ✅ **Generic makes a sound / Rex barks**
- Rex barks / Rex barks
- Error

Explanation: `Dog` **overrides** `speak()`. This is method overriding.

---

**Q8.**
```python
class Counter:
    count = 0
    def __init__(self):
        Counter.count += 1

c1 = Counter()
c2 = Counter()
c3 = Counter()
print(Counter.count)
```
- 1
- 0
- ✅ **3**
- Error

Explanation: `count` is a **class attribute**, shared by all instances — each `__init__` call increments the same shared value.

---

**Q9.**
```python
class Base:
    def __init__(self):
        self.value = 10
        self.setup()
    def setup(self):
        print("Base setup")

class Child(Base):
    def setup(self):
        print("Child setup")

c = Child()
```
- Base setup
- ✅ **Child setup**
- Nothing is printed
- Both "Base setup" and "Child setup"

Explanation: Python resolves `self.setup()` on the **actual object's class** (`Child`) at runtime, even though the call is written inside `Base.__init__`.

---

**Q10.**
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

s = Shape()
```
- Creates an empty Shape object with no error
- ✅ **Raises TypeError: Can't instantiate abstract class Shape with abstract method area**
- Prints "Shape"
- Raises SyntaxError

Explanation: A class with an unimplemented `@abstractmethod` cannot be instantiated directly.

---

## 🍶 Flask / Backend — Project Structure

**Q11.**
```python
# app.py
from flask import Flask
from service import get_all_users

app = Flask(__name__)

@app.route('/users')
def users():
    return get_all_users()

if __name__ == '__main__':
    app.run(debug=True)
```
What is the role of `app.py` here?
- It stores the database schema
- ✅ **It's the entry point — creates the Flask app instance and defines routes, delegating logic to `service.py`**
- It contains all the business logic
- It's the HTML template file

---

**Q12.** In the same file, what does `debug=True` do in `app.run(debug=True)`?
- Makes the app run faster
- ✅ **Enables auto-reload on code changes and shows detailed error tracebacks in the browser**
- Disables all error messages
- Deploys the app to production

---

**Q13.**
```python
# service.py
import sqlite3

def get_all_users():
    conn = sqlite3.connect("app.db")
    cursor = conn.cursor()
    cursor.execute("SELECT * FROM users")
    rows = cursor.fetchall()
    conn.close()
    return {"users": rows}
```
Why is this logic in `service.py` instead of directly in `app.py`?
- Flask requires it
- ✅ **Separation of concerns — routes stay focused on HTTP handling, while `service.py` handles data access/business logic**
- It's not possible to query a database from `app.py`
- `service.py` runs faster than `app.py`

---

**Q14.**
```python
# models.py
class User:
    def __init__(self, id, name, email):
        self.id = id
        self.name = name
        self.email = email

    def to_dict(self):
        return {"id": self.id, "name": self.name, "email": self.email}
```
Why is `to_dict()` needed here?
- To print the object nicely
- ✅ **`jsonify()` can't serialize custom class instances directly — it needs a plain dictionary first**
- To save the object to the database
- To validate the data

---

**Q15.**
```python
@app.route('/users/<int:user_id>', methods=['GET'])
def get_user(user_id):
    user = find_user_by_id(user_id)
    if not user:
        abort(404)
    return jsonify(user.to_dict())
```
What does `<int:user_id>` represent?
- A fixed route name
- ✅ **A dynamic path parameter that captures an integer from the URL (e.g. `/users/5` → `user_id=5`)**
- A query parameter
- A request body field

---

**Q16.** In the same route, what does `abort(404)` do?
- Logs the error and continues normally
- ✅ **Immediately stops the request and returns a 404 Not Found response**
- Deletes the user
- Restarts the Flask server

---

**Q17.**
```python
@app.route('/users', methods=['POST'])
def create_user():
    data = request.json
    if not data.get("name"):
        return jsonify({"error": "name is required"}), 400
    new_user = save_user(data)
    return jsonify(new_user), 201
```
What does the `400` status code indicate here?
- The user was created successfully
- ✅ **Bad Request — the client sent invalid/incomplete data (missing "name")**
- The server crashed
- The user already exists

---

**Q18.** In the same route, what does the `201` status code indicate?
- OK, generic success
- ✅ **Created — a new resource was successfully created**
- Redirect
- Forbidden

---

## 🗄️ SQL — Read the Query

**Q19.**
```sql
SELECT name, COUNT(*) AS total_orders
FROM orders
JOIN users ON orders.user_id = users.id
GROUP BY name
HAVING COUNT(*) > 2
ORDER BY total_orders DESC;
```
What does this query return?
- All users regardless of order count, sorted alphabetically
- ✅ **Each user's name and order count, only for users with more than 2 orders, sorted from highest to lowest count**
- Only users with exactly 2 orders
- All orders with no grouping

---

**Q20.**
```sql
SELECT * FROM products WHERE price > 50 AND stock = 0;
```
What does this query find?
- All products under 50 that are in stock
- ✅ **All products priced above 50 that are out of stock**
- All products regardless of price or stock
- Products with stock greater than 50

---

**Q21.**
```sql
UPDATE users SET is_active = 0 WHERE last_login < '2024-01-01';
```
What would happen if the `WHERE` clause were removed?
- Nothing changes
- The query would fail to run
- ✅ **Every row in the table would be updated, deactivating all users**
- Only the first row would be updated

---

## 🔧 Git — Read the Command Sequence

**Q22.**
```bash
git checkout -b feature-login
# ...make changes, commit...
git checkout main
git merge feature-login
```
What is the correct step-by-step description?
- Deletes `feature-login` and creates `main`
- ✅ **Creates and switches to `feature-login`, work is committed there, then switches back to `main` and merges `feature-login` into it**
- Merges `main` into `feature-login`
- Pushes `feature-login` directly to GitHub

---

**Q23.**
```bash
git add .
git commit -m "fix bug"
git push origin main
```
What is the correct order of what happens to the data?
- Commit → stage → upload
- ✅ **Stage all changes → save as a local commit → upload the commit to the remote `main` branch**
- Upload → stage → commit
- Stage → upload → commit

---

*Total: 24 multiple-choice questions — Python, OOP, Flask/backend architecture, SQL, and Git.*
