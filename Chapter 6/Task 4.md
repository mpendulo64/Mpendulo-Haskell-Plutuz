-- HC6T4: Implement a function to compute the product of elements in a list using foldl
```haskell
-- Product of list elements using foldl
productList :: [Int] -> Int
productList xs = foldl (*) 1 xs
```

### 🧠 Explanation:

- **`foldl (*) 1 xs`**:
  - Starts with an **initial accumulator value** of `1`.
  - Applies the **multiplication operator (`*`)** from **left to right** across the list.
  - Combines each element with the running total.




