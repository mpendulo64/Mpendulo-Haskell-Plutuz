-- HC6T10: Implement a recursive function that takes a number and returns a list of its digits.

```haskell
-- Convert a number to a list of its digits
digits :: Int -> [Int]
digits n
    | n < 10    = [n]
    | otherwise = digits (n `div` 10) ++ [n `mod` 10]
```

### 🧠 Explanation:

- **Base Case**:
  - If `n < 10`, it's a single-digit number, so just return `[n]`.

- **Recursive Case**:
  - `digits (n div 10)` recursively processes the number without its last digit.
  - `n mod 10` gives the last digit.
  - `++ [n mod 10]` appends the last digit at the end of the result.




