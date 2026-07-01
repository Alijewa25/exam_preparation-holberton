## 🐍 Python — Dictionaries

**43. How to access a value with `dict[key]`?**
```python
person = {"name": "Ali", "age": 25}
print(person["name"])   # Ali
```
Directly returns the value for that key.
 
**44. Difference between `dict[key]` and `dict.get(key, default)`?**
`dict[key]` raises a `KeyError` if the key doesn't exist. `dict.get(key, default)` returns the value if it exists, or the **default value** (or `None` if no default given) if the key is missing — no error.
 
**45. How to access a value in a nested dictionary? Example.**
```python
data = {"user": {"name": "Ali", "address": {"city": "Baku"}}}
print(data["user"]["address"]["city"])   # Baku
```
Chain the keys with square brackets.
 
---