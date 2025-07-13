HC12T4
Write a program that calculates and prints the first 10 Fibonacci numbers using recursion.
---



```haskell
-- Recursive Fibonacci function
fib :: Int -> Int
fib n
    | n == 0    = 0
    | n == 1    = 1
    | otherwise = fib (n - 1) + fib (n - 2)

-- Print the first 10 Fibonacci numbers
main :: IO ()
main = do
    let limit = 10
    let fibList = [fib n | n <- [0..(limit - 1)]]
    putStrLn "🌀 First 10 Fibonacci numbers (recursive):"
    print fibList
```

---

### 🧠 Explanation

- **`fib :: Int -> Int`**  
  A recursive function:
  - Base cases: `fib 0 = 0`, `fib 1 = 1`
  - Recursive case: `fib n = fib(n - 1) + fib(n - 2)`

- **List comprehension**:  
  - `[fib n | n <- [0..(limit - 1)]]` builds the list of the first 10 Fibonacci numbers.
  - `limit - 1` ensures we include index `0` through `9`.

- **`print fibList`**:  
  Displays the list directly.

---

