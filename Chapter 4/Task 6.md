HC4T6 - Task 6: Identify List Contents Using Pattern Matching
```haskell
-- Function to describe what's inside a list based on its length
whatsInsideThisList :: [a] -> String
whatsInsideThisList []       = "The list is empty."
whatsInsideThisList [x]      = "The list has one element."
whatsInsideThisList [x, y]   = "The list has two elements."
whatsInsideThisList (_:_:_:_) = "The list has many elements."
```

---

### 🧠 Explanation

- The function has the type `[a] -> String`, meaning it takes a list of any type (`[a]`) and returns a `String`.
- Pattern matching is used to match different list shapes:
  - `[]` matches an empty list.
  - `[x]` matches a list with exactly one element.
  - `[x, y]` matches a list with exactly two elements.
  - `(_:_:_:_)` matches any list with three or more elements (we use wildcards `_` to ignore the actual values).

---
