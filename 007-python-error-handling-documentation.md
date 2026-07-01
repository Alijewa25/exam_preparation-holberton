## 🐍 Python — Error Handling & Documentation
 
**46. Purpose of `try`/`except`?**
`try` contains code that might raise an error; `except` catches and handles that error **without crashing the program**.
 
**47. What does `finally` do?**
Contains code that **always runs**, whether an exception occurred or not (e.g. for cleanup like closing a file).
 
**48. What does `raise` do?**
Manually **triggers/throws** an exception, either built-in or custom.
 
**49. Two built-in exceptions?**
- `ValueError` — raised when a function receives an argument of the right type but an invalid value (e.g. `int("abc")`).
- `ZeroDivisionError` — raised when dividing by zero (e.g. `10 / 0`).
- (Also common: `TypeError` — wrong type used in an operation; `KeyError` — dictionary key not found.)
**50. What is a docstring? What is PEP 257?**
A docstring is a string literal placed right after a `def`, `class`, or at the top of a module to **document what it does**. PEP 257 is the official Python style guide that defines **conventions for writing docstrings**.
 
**51. Module-level vs function-level docstring?**
A **module-level** docstring is placed at the **very top of a `.py` file** and describes the purpose of the whole file/module. A **function-level** docstring is placed **inside a function**, right after `def`, describing what that specific function does, its parameters, and return value.