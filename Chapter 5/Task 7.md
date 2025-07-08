HC5T7: The $ Operator

---



```haskell
-- Using the $ operator to simplify nested function calls
result :: Int
result = sum $ map (*2) $ filter (>3) [1..10]
```

---

### 🧠 Explanation

- Original expression:
  ```haskell
  result = sum (map (*2) (filter (>3) [1..10]))
  ```
  This applies `filter`, then `map`, then `sum`, using nested parentheses.

- Rewritten with `$`:
  ```haskell
  result = sum $ map (*2) $ filter (>3) [1..10]
  ```

- The `$` operator is right-associative and low-precedence. It lets you eliminate parentheses by saying:
  ```haskell
  f $ g x = f (g x)
  ```

- So this reads as:
  - Filter numbers greater than 3 from `[1..10]`
  - Double each of those numbers
  - Sum the result

---

### 🧪 Example Output

```haskell
*Main> result
84
```

