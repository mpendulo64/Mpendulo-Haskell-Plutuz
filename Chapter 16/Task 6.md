HC16T6: Implement a function that returns the nth Fibonacci number.
---



```haskell
-- Recursive Fibonacci function
fibonacci :: Int -> Int
fibonacci n
    | n < 0     = error "❌ Negative index is not allowed in Fibonacci sequence."
    | n == 0    = 0
    | n == 1    = 1
    | otherwise = fibonacci (n - 1) + fibonacci (n - 2)

-- Main function to demonstrate usage
main :: IO ()
main = do
    putStrLn "🔢 Enter the position (n) of Fibonacci number:"
    input <- getLine
    let n = read input :: Int
    let fibN = fibonacci n
    putStrLn $ "🧮 The " ++ show n ++ "th Fibonacci number is: " ++ show fibN
```

---

### 🧠 Explanation

- **Base cases**:
  - `fibonacci 0 = 0`
  - `fibonacci 1 = 1`

- **Recursive case**:
  - `fibonacci n = fibonacci(n - 1) + fibonacci(n - 2)`

- **Error check**:
  - The function will raise an error if a negative index is provided, since negative Fibonacci numbers aren't typically defined.

- **Main function**:
  - Prompts user for input.
  - Parses input and calls `fibonacci`.
  - Outputs the result in a friendly format.

---

