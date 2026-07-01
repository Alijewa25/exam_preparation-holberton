## 🐍 Python — Conditionals & Loops

**26. Difference between `if`, `elif`, `else`?**
`if` checks a condition; `elif` (else if) checks another condition **only if the previous ones were false**; `else` runs if **none** of the above conditions were true.
 
**27. What do `and`, `or`, `not` do?**
`and` → True only if **both** conditions are true (`True and False` → `False`).
`or` → True if **at least one** condition is true (`True or False` → `True`).
`not` → **reverses** a boolean value (`not True` → `False`).
 
**28. Difference between `is` and `==`?**
`==` compares **values** (are they equal?). `is` compares **identity** (are they the exact same object in memory?). Example: `[1,2] == [1,2]` → `True`, but `[1,2] is [1,2]` → `False`.
 
**29. What does `range(5)` produce? `range(2, 10, 2)`?**
`range(5)` → `0, 1, 2, 3, 4` (start=0 default, stop=5, step=1 default).
`range(2, 10, 2)` → `2, 4, 6, 8` (start=2, stop=10 exclusive, step=2).
 
**30. Difference between `for` and `while` loop?**
`for` loops iterate over a **known sequence** (list, range, string, etc.) a fixed number of times. `while` loops repeat **as long as a condition is true**, useful when the number of iterations isn't known in advance.
 
**31. What does `break` do?**
Immediately **exits** the loop entirely, skipping any remaining iterations.
 
**32. What does `continue` do?**
**Skips** the rest of the current iteration and moves to the **next** iteration of the loop.