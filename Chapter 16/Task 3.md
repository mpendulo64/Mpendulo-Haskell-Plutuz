 HC16T3: Define a function to calculate the factorial of a number.
---



```haskell
-- Recursive factorial function
factorial :: Integer -> Integer
factorial n
    | n < 0     = error "❌ Factorial is not defined for negative numbers."
    | n == 0    = 1
    | otherwise = n * factorial (n - 1)

-- Main function to demonstrate usage
main :: IO ()
main = do
    putStrLn "📥 Enter a non-negative integer:"
    input <- getLine
    let number = read input :: Integer
    let result = factorial number
    putStrLn $ "🧮 Factorial of " ++ show number ++ " is " ++ show result
```

---

### 🧠 Explanation

- **Function Signature**  
  `factorial :: Integer -> Integer` uses `Integer` to support very large values, unlike `Int` which can overflow.

- **Guard Conditions**  
  - `n < 0`: throws a descriptive error.
  - `n == 0`: base case returns 1.
  - `otherwise`: recursive call builds the product `n * factorial (n - 1)`.

- **`main` Function**  
  - Prompts the user.
  - Converts input to `Integer`.
  - Computes the factorial and displays the result.

---

