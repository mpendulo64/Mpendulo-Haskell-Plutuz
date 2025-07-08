HC4T8 - Task 8: Extract Values from Tuples

---



```haskell
-- Function to describe a tuple of two elements
describeTuple :: (Show a, Show b) => (a, b) -> String
describeTuple (x, y) = "The first value is " ++ show x ++ " and the second value is " ++ show y ++ "."
```

---

### 🧠 Explanation

- `describeTuple :: (Show a, Show b) => (a, b) -> String`:
  - The function takes a tuple of two elements `(a, b)` where both `a` and `b` are types that can be converted to strings using `show`.
  - The `Show a, Show b` constraint ensures that the values can be displayed as strings.
- `(x, y)` pattern matches the two elements of the tuple.
- `show x` and `show y` convert the values to strings for concatenation.

---

