## 🐍 Python — Functions

**33. Basic syntax to define a function?**
```python
def function_name(parameters):
    # code
    return value
```
 
**34. What is a default parameter? Example?**
A parameter that has a **preset value** used if no argument is passed for it.
```python
def greet(name="Guest"):
    print(f"Hello, {name}")
 
greet()        # Hello, Guest
greet("Ali")   # Hello, Ali
```
 
**35. What does `return` do? What if there's no `return`?**
`return` sends a value back to the caller and **ends** the function's execution. If there's no `return`, the function automatically returns `None`.
 
**36. Difference between calling a function `func()` and referencing it `func`?**
`func()` **executes** the function and returns its result. `func` (without parentheses) refers to the **function object itself** — it can be stored in a variable or passed to another function without running it.