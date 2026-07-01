# Code Analysis — Exam Prep (Code Reading & Project Structure Q&A)

This file simulates the type of questions you might get on the exam: **"here's some code, what does it do / what does it output / what's wrong with it?"** — plus questions about typical project architecture (`app.py`, `service.py`, `models.py`, etc.).

---

## 🐍 Python — Predict the Output

**1.**
```python
x = 5
y = x
x = 10
print(y)
```
**Question:** What is printed, and why?
**Answer:** `5`. Integers are immutable — `y = x` copied the **value** at that moment. Reassigning `x` doesn't affect `y`.

---

**2.**
```python
a = [1, 2, 3]
b = a
b.append(4)
print(a)
```
**Question:** What is printed, and why?
**Answer:** `[1, 2, 3, 4]`. Lists are mutable, and `b = a` made `b` **reference the same list object** as `a`. Modifying `b` also changes `a`.

---

**3.**
```python
def add_item(item, lst=[]):
    lst.append(item)
    return lst

print(add_item(1))
print(add_item(2))
```
**Question:** What is printed on each call, and why?
**Answer:** `[1]` then `[1, 2]`. This is the classic **mutable default argument bug** — the default list `[]` is created **once**, when the function is defined, and reused across calls instead of being reset each time.

---

**4.**
```python
for i in range(3):
    if i == 1:
        continue
    print(i)
```
**Question:** What is printed?
**Answer:** `0` then `2`. When `i == 1`, `continue` skips the `print(i)` for that iteration and moves to the next.

---

**5.**
```python
print(1 == 1.0)
print(1 is 1.0)
```
**Question:** What do these two lines print, and why are they different?
**Answer:** `True` then `False`. `==` compares **value** (1 equals 1.0 numerically). `is` compares **identity/object type** — an `int` and a `float` are different objects, so `is` is `False`.

---

**6.**
```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
finally:
    print("Done")
```
**Question:** What is the output?
**Answer:**
```
Cannot divide by zero
Done
```
The `except` block catches the error and prints its message; `finally` **always runs** afterward regardless of whether an exception occurred.

---

**7.**
```python
d = {"a": 1, "b": 2}
print(d.get("c", 0))
print(d["c"])
```
**Question:** What happens on each line?
**Answer:** First line prints `0` (key `"c"` doesn't exist, so `.get()` returns the default). Second line **raises a `KeyError`**, because `dict[key]` doesn't accept a default and crashes if the key is missing.

---

## 🧱 OOP — Read & Explain

**8.**
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
**Question:** What is printed, and what OOP concept does `Dog.speak()` demonstrate?
**Answer:**
```
Generic makes a sound
Rex barks
```
`Dog` **overrides** the `speak()` method inherited from `Animal` — this is **method overriding**.

---

**9.**
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
**Question:** What is printed, and why?
**Answer:** `3`. `count` is a **class attribute**, shared across all instances. Each time `__init__` runs, it increments the **same shared** `Counter.count`, not an instance copy.

---

**10.**
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
**Question:** What is printed, and why (even though `setup` is only explicitly called inside `Base.__init__`)?
**Answer:** `Child setup`. Even though `self.setup()` is called from `Base.__init__`, Python looks up the method on the **actual object's class** (`Child`) first — this is dynamic method resolution / polymorphism, not the literal class where the call is written.

---

**11.**
```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

s = Shape()
```
**Question:** What happens when this code runs, and why?
**Answer:** It raises `TypeError: Can't instantiate abstract class Shape with abstract method area`. Because `Shape` has an `@abstractmethod` that isn't implemented, it **cannot be instantiated directly** — it must be subclassed with `area()` implemented.

---

## 🍶 Flask / Backend — Explain the Code & Project Structure

**12.**
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
**Question:** What is the role of `app.py` here, and what does `debug=True` do?
**Answer:** `app.py` is the **entry point** of the Flask application — it creates the Flask app instance and defines the routes (URL → function mapping). It imports the actual logic (`get_all_users`) from another file rather than writing business logic directly in the route. `debug=True` enables Flask's **debug mode**: auto-reloads the server on code changes and shows detailed error tracebacks in the browser (should be `False` in production).

---

**13.**
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
**Question:** What is the purpose of `service.py` in this project structure? Why isn't this logic written directly inside `app.py`?
**Answer:** `service.py` contains the **business logic / data-access layer** — in this case, querying the database and returning the results. It's separated from `app.py` (the routing layer) to follow **separation of concerns**: routes stay clean and only handle HTTP request/response, while `service.py` handles *how* the data is actually fetched/processed. This makes the code more organized, reusable, and easier to test.

---

**14.**
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
**Question:** What is the role of a `models.py` file in a typical backend project? What does `to_dict()` do here, and why might it be needed?
**Answer:** `models.py` defines the **data structures/entities** of the application (here, a `User`) — usually mapping to database tables. `to_dict()` converts the object into a plain dictionary, which is needed because Flask's `jsonify()` can't directly serialize custom class instances to JSON — it needs a dict first.

---

**15.**
```python
@app.route('/users/<int:user_id>', methods=['GET'])
def get_user(user_id):
    user = find_user_by_id(user_id)
    if not user:
        abort(404)
    return jsonify(user.to_dict())
```
**Question:** Explain what this route does, piece by piece.
**Answer:** `<int:user_id>` is a **dynamic path parameter** that captures an integer from the URL (e.g. `/users/5` → `user_id=5`). The function looks up the user by that ID. If no user is found, `abort(404)` immediately returns a "Not Found" error. Otherwise, it converts the user object to a dictionary and returns it as a JSON response via `jsonify()`.

---

**16.**
```python
@app.route('/users', methods=['POST'])
def create_user():
    data = request.json
    if not data.get("name"):
        return jsonify({"error": "name is required"}), 400
    new_user = save_user(data)
    return jsonify(new_user), 201
```
**Question:** What does this route do? What do the `400` and `201` mean here?
**Answer:** It creates a new user from JSON sent in the request body. It first validates that `"name"` was provided — if not, it returns an error with status **400 (Bad Request)**. If valid, it saves the user and returns the new user data with status **201 (Created)**, indicating a resource was successfully created.

---

## 🗄️ SQL — Read the Query

**17.**
```sql
SELECT name, COUNT(*) AS total_orders
FROM orders
JOIN users ON orders.user_id = users.id
GROUP BY name
HAVING COUNT(*) > 2
ORDER BY total_orders DESC;
```
**Question:** In plain English, what does this query return?
**Answer:** It returns each user's **name** and their **total number of orders**, but only for users who have placed **more than 2 orders**, sorted from the **highest** order count to the lowest. The `JOIN` connects `orders` to `users` via `user_id`.

---

**18.**
```sql
SELECT * FROM products WHERE price > 50 AND stock = 0;
```
**Question:** What does this query find?
**Answer:** All products that cost **more than 50** and are **out of stock** (`stock = 0`).

---

**19.**
```sql
UPDATE users SET is_active = 0 WHERE last_login < '2024-01-01';
```
**Question:** What does this statement do? What could go wrong if `WHERE` is forgotten?
**Answer:** It deactivates (`is_active = 0`) all users whose last login was before Jan 1, 2024. If the `WHERE` clause is forgotten, the `UPDATE` would apply to **every row in the table**, deactivating all users — a common and dangerous mistake.

---

## 🔧 Git — Read the Command Sequence

**20.**
```bash
git checkout -b feature-login
# ...make changes, commit...
git checkout main
git merge feature-login
```
**Question:** What is happening in this sequence, step by step?
**Answer:** 1) Creates and switches to a new branch called `feature-login`. 2) Work is done and committed on that branch. 3) Switches back to the `main` branch. 4) Merges the changes from `feature-login` into `main`, combining the two histories.

---

**21.**
```bash
git add .
git commit -m "fix bug"
git push origin main
```
**Question:** What does each command do, and in what order does data move from local to remote?
**Answer:** `git add .` **stages** all changed files. `git commit -m "..."` **saves** the staged changes as a new commit in the local repository, with a message. `git push origin main` **uploads** those local commits to the `main` branch of the remote repository (`origin`, e.g. GitHub).

---