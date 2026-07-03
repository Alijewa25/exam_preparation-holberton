# Holberton Quiz Bank — Real Exam-Style Questions (with Answers)

These are actual multiple-choice questions from Holberton, provided as-is. Correct answer(s) are marked with ✅ and briefly explained.

---

## 🐍 Conditionals & Loops

**Q0.** What do these lines print?
```python
if True:
    print("Holberton")
else:
    print("School")
```
✅ **Holberton** — the condition `True` is always true.

---

**Q1.**
```python
if 12 == 48/4:
    print("Holberton")
else:
    print("School")
```
✅ **Holberton** — `48/4 = 12.0`, and `12 == 12.0` is `True`.

---

**Q2.**
```python
if 12 == 48/4 and False:
    print("Holberton")
else:
    print("School")
```
✅ **School** — `True and False` = `False`, so the `else` branch runs.

---

**Q3.**
```python
if 12 == 48/3 or 12 is 12:
    print("Holberton")
else:
    print("School")
```
✅ **Holberton** — `48/3 = 16.0`, so `12 == 16.0` is `False`, but `12 is 12` is `True` (small integers are cached/interned in CPython). `False or True` = `True`.

---

**Q4.**
```python
a = 12
if a > 2:
    if a % 2 == 0:
        print("Holberton")
    else:
        print("C is fun")
else:
    print("School")
```
✅ **Holberton** — `a > 2` is `True`, and `a % 2 == 0` is `True` (12 is even).

---

**Q5.**
```python
a = 12
if a < 2:
    print("Holberton")
elif a % 2 == 0:
    print("C is fun")
else:
    print("School")
```
✅ **C is fun** — `a < 2` is `False`, so it checks `elif a % 2 == 0`, which is `True`.

---

**Q6.**
```python
for i in range(4):
    print(i, end=" ")
```
✅ **0 1 2 3** — `range(4)` goes from `0` to `3` (stop is exclusive).

---

**Q7.**
```python
for i in range(2, 4):
    print(i, end=" ")
```
✅ **2 3** — starts at `2`, stops before `4`.

---

**Q8.**
```python
for i in range(2, 10, 2):
    print(i, end=" ")
```
✅ **2 4 6 8** — starts at `2`, stops before `10`, step of `2`.

---

## 🐍 Functions

**Q0.**
```python
def my_function():
    print("In my function")

my_function()
```
✅ **In my function** — the function is **called** (with `()`), so its body executes.

---

**Q1.**
```python
def my_function():
    print("In my function")

my_function
```
✅ **function my_function at ...** — without `()`, this only references the **function object itself** (not called), so in an interactive shell it displays the function's repr.

---

**Q2.**
```python
def my_function(counter):
    print("Counter: {}".format(counter))

my_function(12)
```
✅ **Counter: 12** — `12` is passed as the `counter` argument and inserted into the string.

---

**Q3.**
```python
def my_function(counter=89):
    print("Counter: {}".format(counter))

my_function(12)
```
✅ **Counter: 12** — the passed argument `12` **overrides** the default value `89`.

---

**Q4.**
```python
def my_function(counter=89):
    print("Counter: {}".format(counter))

my_function()
```
✅ **Counter: 89** — no argument passed, so the **default value** is used.

---

**Q5.**
```python
def my_function(counter=89):
    return counter + 1

print(my_function())
```
✅ **90** — `counter` defaults to `89`, and the function returns `89 + 1`.

---

## 🐍 Lists

**Q0.** `a = [1, 2, 3, 4]` → `a[0]`
✅ **1** — index `0` is the first element.

**Q1.** `a[-1]`
✅ **4** — negative index `-1` is the last element.

**Q2.** `a[-3]`
✅ **2** — counting backward: `-1`→4, `-2`→3, `-3`→2.

**Q3.** `len(a)`
✅ **4** — the list has 4 elements.

**Q4.** `a.append(5)` then `len(a)`
✅ **5** — one element was added, so length increases from 4 to 5.

**Q5.** `a[1:3]`
✅ **[2, 3]** — slice from index 1 up to (not including) index 3.

**Q6.** `a[2] = 10` then `a`
✅ **[1, 2, 10, 4]** — index 2 (the third element, value `3`) is replaced with `10`.

**Q7.** `b = a` then `b`
✅ **[1, 2, 3, 4]** — `b` now references the same list, currently holding the original values.

**Q8.** `b = a`, `a[2] = 10`, then `a`
✅ **[1, 2, 10, 4]** — `a` was directly modified.

**Q9.** `b = a`, `a[2] = 10`, then `b`
✅ **[1, 2, 10, 4]** — since `b` and `a` **reference the same list object**, modifying `a` also changes what `b` shows. This is the reference-vs-copy concept.

---

## 🐍 Dictionaries

**Q0.** `a = {'id': 89, 'name': "John"}` → `a['id']`
✅ **89**

**Q1.** `a.get('id')`
✅ **89**

**Q2.** `a.get('age')`
✅ **Nothing** — key doesn't exist and no default was given, so `.get()` returns `None` (displayed as nothing/blank).

**Q3.** `a.get('age', 0)`
✅ **0** — the given default value is returned since `'age'` doesn't exist.

**Q4.** `a = {'id': 89, 'name': "John", 'projects': [1, 2, 3, 4]}` → `a.get('projects')`
✅ **[1, 2, 3, 4]**

**Q5.** `a.get('projects')[3]`
✅ **4** — index `3` of the list `[1, 2, 3, 4]`.

**Q6.** `a.get('friends')[-1].get("name")` where `friends = [{'id': 82, 'name': "Bob"}, {'id': 83, 'name': "Amy"}]`
✅ **Amy** — `[-1]` gets the last friend dict (Amy's), then `.get("name")` retrieves her name.

**Q7.** `for i in range(0, 3): print(i, end=" ")`
✅ **0 1 2**

**Q8.** `for i in range(1, 4): print(i, end=" ")`
✅ **1 2 3**

**Q9.** `for i in [1, 2, 3, 4]: print(i, end=" ")`
✅ **1 2 3 4**

**Q10.** `for i in [1, 3, 4, 2]: print(i, end=" ")`
✅ **1 3 4 2** — iterates in list order, not sorted.

**Q11.** `for i in ["Hello", "Holberton", "School", 98]: print(i, end=" ")`
✅ **Hello Holberton School 98**

---

## 🧱 OOP — `class User`

```python
class User:
    id = 89
    name = "no name"
    __password = None

    def __init__(self, new_name=None):
        self.is_new = True
        if new_name is not None:
            self.name = new_name
```

**Q0.** What is `User`?
✅ **A class**

**Q1.** What is `id`?
✅ **A public class attribute** — defined directly in the class body, no underscore prefix, shared across instances unless overridden.

**Q2.** What is `__password`?
✅ **A private class attribute** — double-underscore prefix triggers name mangling, restricting outside access.

**Q3.** What is `is_new`?
✅ **A public instance attribute** — defined via `self.is_new` inside `__init__`, unique to each instance.

**Q4.** `u = User()` → `u.is_new`
✅ **True** — always set to `True` in `__init__`.

**Q5.** `u = User()` → `u.id`
✅ **89** — inherited from the class attribute, since no instance-level `id` was set.

**Q6.** `u = User("John")` → `u.name`
✅ **John** — `new_name` was passed, so `self.name` is set to `"John"` inside `__init__`.

**Q7.** `u = User()` → `u.name`
✅ **no name** — no `new_name` passed, so the class attribute default `"no name"` applies.

---

## 🗄️ SQL Basics

**Q0.** What does SQL stand for?
✅ **Structured Query Language**

**Q1.** What is a relational database? *(select all correct)*
✅ **a database** · **a collection of data** · **data are organized by tables, records and columns**
❌ "married databases" (nonsense distractor), "data are organized by tables and indexes" (indexes are a performance feature, not the defining structure), "table containing multiple/only one object representation" (not accurate definitions).

**Q2.** What does DDL stand for?
✅ **Data Definition Language**

**Q3.** What does DML stand for?
✅ **Data Manipulation Language**

**Q4.** How do you list all users in the `users` table?
✅ `SELECT * FROM users;`

**Q5.** How do you add a new record to `users (id, name, age)`?
✅ `INSERT INTO users (id, name, age) VALUES (2, "Betty", 30);`
(Other options either omit `INTO`, mismatch column count and values, or drop a required value.)

**Q6.** How do you delete the record with `id = 89`?
✅ `DELETE FROM users WHERE id = 89;`

**Q7.** How do you change the name of the record with `id = 89` to `"Holberton"`?
✅ `UPDATE users SET name = "Holberton" WHERE id = 89;`

**Q8.** How do you list all records with `age > 21`?
✅ `SELECT * FROM users WHERE age > 21;`

---

## 🔐 DCL (Data Control Language) & Permissions

**Q0.** What does DCL mean?
✅ **Data Control Language**

**Q1.** Can you give only read access to a database to a user?
✅ **Yes**

**Q2.** Can you give only read access to a table to a user?
✅ **Yes**

**Q3.** Can you give only read access to multiple databases and tables?
✅ **Yes**

**Q4.** Can you give only delete access to a table?
✅ **Yes**

**Q5.** Can you give only insert access to a table?
✅ **Yes**
(SQL privileges via `GRANT` are granular — `SELECT`, `INSERT`, `UPDATE`, `DELETE` can each be granted independently, on databases or specific tables.)

**Q6.** Which JOIN type doesn't exist? *(select all correct)*
✅ **IN LEFT** · **RIGHT AND LEFT** · **TOP** · **FULL INNER**
❌ Real JOIN types that DO exist (not selected): `LEFT`, `RIGHT`, `INNER`, `FULL OUTER`.

---

*This file reflects real Holberton quiz content shared directly by the mentor. Cross-reference with `003`–`010` for deeper explanations of the same concepts.*