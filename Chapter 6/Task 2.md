HC6T2: Implement a recursive function to compute the nth Fibonacci number.
```haskell
-- Recursive function to compute the nth Fibonacci number
fib :: Int -> Int
fib 0 = 0
fib 1 = 1
fib n = fib (n - 1) + fib (n - 2)
```

### 🧠 Explanation:
- **Base Cases**:
  - `fib 0 = 0` means if the input is 0, return 0.
  - `fib 1 = 1` means if the input is 1, return 1.
- **Recursive Case**:
  - For any `n > 1`, the function calls itself twice: once with `(n - 1)` and once with `(n - 2)`. This mirrors the Fibonacci definition:  
    $$ F(n) = F(n - 1) + F(n - 2) $$

