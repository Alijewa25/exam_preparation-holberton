## 🐍 Python — Lists

**37. Positive vs negative indexing?**
Positive indexing starts from `0` at the beginning: `my_list[0]` is the first item. Negative indexing starts from `-1` at the end: `my_list[-1]` is the last item.
 
**38. What is slicing? `my_list[1:4]`?**
Slicing extracts a **sub-part** of a list using `[start:stop]` (stop is exclusive). For `my_list = [10,20,30,40,50]`, `my_list[1:4]` → `[20, 30, 40]`.
 
**39. What does `.append()` do?**
Adds a single item to the **end** of the list.
 
**40. Difference between `.remove()` and `.pop()`?**
`.remove(value)` deletes the **first occurrence of a specific value**. `.pop(index)` removes and **returns** the item at a given index (default: last item).
 
**41. What does `.sort()` do? Original or new list?**
Sorts the list **in place** (modifies the original list) and returns `None`. (Use `sorted()` if you want a new sorted list instead.)
 
**42. Difference between `b = a` and `b = a.copy()`?**
`b = a` makes `b` **point to the same list object** as `a` — changing one changes the other (reference). `b = a.copy()` creates a **new, independent list** with the same values — changing one does **not** affect the other.