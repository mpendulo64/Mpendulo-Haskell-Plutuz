HC4T7 - Task 7: Ignore Elements in a List

---



```haskell
-- Function to return the first and third elements of a list
firstAndThird :: [a] -> [a]
firstAndThird (x:_:z:_) = [x, z]
firstAndThird _         = []
```

---

### 🧠 Explanation

- `firstAndThird :: [a] -> [a]`: The function takes a list of any type and returns a list containing just the first and third elements.
- `(x:_:z:_)` pattern:
  - `x` binds to the first element.
  - `_` ignores the second element.
  - `z` binds to the third element.
  - `_` ignores the rest of the list.
- The second clause `_` matches any list that doesn't have at least three elements and returns an empty list.

---
