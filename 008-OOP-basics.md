##  OOP Basics

**1. What is a class? How do you define one?**
A class is a **blueprint/template** for creating objects — it defines attributes (data) and methods (behavior).
```python
class Dog:
    pass
```
 
**2. What is `self`?**
`self` refers to the **current instance** of the class — it's how a method accesses and modifies that specific object's attributes. It's automatically passed as the first argument to instance methods.
 
**3. What is `__init__`?**
The **constructor** method — automatically called when a new object is created. It's used to initialize instance attributes.
```python
class Dog:
    def __init__(self, name):
        self.name = name
```
 
**4. Difference between class attribute and instance attribute?**
A **class attribute** is defined directly inside the class body and is **shared by all instances**. An **instance attribute** is defined inside `__init__` (via `self.attr = ...`) and is **unique to each object**.
```python
class Dog:
    species = "Canine"        # class attribute
    def __init__(self, name):
        self.name = name      # instance attribute
```
 
**5. Public, protected (`_`), private (`__`) attributes?**
- **Public** (`self.name`): accessible from anywhere, no restriction.
- **Protected** (`self._name`): a **convention** signaling "internal use only" — still accessible, but shouldn't be accessed outside the class/subclasses.
- **Private** (`self.__name`): triggers **name mangling**, making it harder to access directly from outside the class.
**6. What is name mangling?**
When an attribute starts with `__` (double underscore, no trailing `__`), Python internally renames it to `_ClassName__attribute` to avoid accidental access/override from outside or in subclasses. Example: `self.__name` inside class `Dog` becomes `_Dog__name`.
 
**7. What do `__str__`, `__repr__`, `__del__`, `__doc__` do?**
- `__str__` — defines the **user-friendly** string shown by `print(obj)` or `str(obj)`.
- `__repr__` — defines the **developer/debug** string representation, shown in the console or by `repr(obj)`; should ideally be unambiguous.
- `__del__` — called when an object is **about to be destroyed** (garbage collected) — a destructor.
- `__doc__` — holds the **docstring** of the class/function/module.
**8. Instance attribute vs class attribute — lookup order?**
When you access `obj.attribute`, Python first looks in the **instance's own `__dict__`**. If not found there, it looks in the **class** (and then parent classes). So an instance attribute **shadows/overrides** a class attribute of the same name for that specific object.