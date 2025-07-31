HC17T5: Implement a function combineLists that uses the Semigroup instance to concatenate two lists of integers.




```haskell
-- Define the combineLists function
combineLists :: [Int] -> [Int] -> [Int]
combineLists xs ys = xs <> ys  -- uses Semigroup instance for lists

-- Example usage
main :: IO ()
main = do
    let listA = [1, 2, 3]
    let listB = [4, 5, 6]

    putStrLn $ "📦 Combined list: " ++ show (combineLists listA listB)
```

---

### 🧠 Explanation

- **`Semigroup [a]`**: Lists are an instance of `Semigroup` where `(<>)` is defined as list concatenation.
- **Function `combineLists`**:
  - Takes two `[Int]` and combines them using `<>`.
- **Result**:
  - `[1, 2, 3] <> [4, 5, 6]` yields `[1, 2, 3, 4, 5, 6]`.

