##  OOP Advanced

**9. What is inheritance? `class Child(Parent)`?**
Inheritance lets a class (**child/subclass**) reuse and extend the attributes and methods of another class (**parent/superclass**). `class Child(Parent):` means `Child` inherits everything from `Parent`.
 
**10. What does `super().__init__()` do? Why does calling order matter?**
`super()` gives access to the **parent class**, so `super().__init__()` calls the parent's constructor — commonly used to initialize inherited attributes before adding child-specific ones. Calling order matters because if you access `self` attributes **before** calling `super().__init__()`, those parent-initialized attributes won't exist yet, causing errors.
```python
class Animal:
    def __init__(self, name):
        self.name = name
 
class Dog(Animal):
    def __init__(self, name, breed):
        super().__init__(name)   # must run first to set self.name
        self.breed = breed
```
 
**11. What is method overriding?**
When a subclass defines a method with the **same name** as one in its parent class, replacing (overriding) the parent's behavior for that subclass.
 
**12. What is multiple inheritance?**
When a class inherits from **more than one parent class** at the same time.
```python
class C(A, B):
    pass
```
Python resolves conflicts using the **MRO (Method Resolution Order)**.
 
**13. What do `isinstance()` and `issubclass()` do?**
`isinstance(obj, Class)` checks if `obj` is an **instance** of `Class` (or its subclasses) — returns True/False. `issubclass(ClassA, ClassB)` checks if `ClassA` is a **subclass** of `ClassB`.
 
**14. What is the `abc` module? `ABC`, `@abstractmethod`?**
The `abc` module lets you create **abstract base classes** — classes that can't be instantiated directly and are meant to be subclassed. `ABC` is the base class to inherit from. `@abstractmethod` marks a method that **must be implemented** by any concrete subclass, or Python raises an error.
```python
from abc import ABC, abstractmethod
 
class Shape(ABC):
    @abstractmethod
    def area(self):
        pass
```
 
**15. What is duck typing?**
A concept where Python doesn't check an object's **type**, but whether it has the **methods/behavior** needed ("if it walks like a duck and quacks like a duck, it's a duck"). Focuses on behavior over explicit type.
 
**16. What is the mixin pattern?**
A **mixin** is a small class designed to provide extra, reusable functionality to other classes via multiple inheritance, without being meant to stand alone as a full class. It "mixes in" behavior.
```python
class JSONMixin:
    def to_json(self):
        import json
        return json.dumps(self.__dict__)
 
class User(JSONMixin):
    def __init__(self, name):
        self.name = name
```
 
**17. What does subclassing `list` or `dict` mean?**
Creating a custom class that **inherits from** the built-in `list` or `dict` type, so it behaves like a list/dict but can have extra custom methods or overridden behavior.
```python
class MyList(list):
    def last(self):
        return self[-1]
```
 
**18. What is a custom iterator? `__iter__`, `__next__`?**
A custom iterator is a class that defines its own iteration behavior for use in `for` loops. `__iter__` returns the **iterator object itself** (usually `self`). `__next__` returns the **next value** in the sequence, and raises `StopIteration` when there are no more items.
```python
class Counter:
    def __init__(self, limit):
        self.n = 0
        self.limit = limit
    def __iter__(self):
        return self
    def __next__(self):
        if self.n < self.limit:
            self.n += 1
            return self.n
        raise StopIteration
```