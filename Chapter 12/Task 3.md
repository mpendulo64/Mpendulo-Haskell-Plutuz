HC12T3
Create a program that defines a function factorial to compute the factorial of a given positive integer.
---



```haskell
-- Factorial program in Haskell

-- Recursive function to compute factorial
factorial :: Int -> Int
factorial n
    | n == 0    = 1          -- base case: 0! = 1
    | n > 0     = n * factorial (n - 1)  -- recursive case
    | otherwise = error "❌ Input must be a non-negative integer"

-- Main function to test it
main :: IO ()
main = do
    putStrLn "📥 Enter a positive integer:"
    input <- getLine
    let number = read input :: Int
    let result = factorial number
    putStrLn $ "🧮 The factorial of " ++ show number ++ " is " ++ show result
```

---

### 🧠 Explanation

- **`factorial :: Int -> Int`**:  
  Declares a function that takes an integer and returns its factorial.

- **Guards (`|`)**:  
  Provide conditions:
  - If `n == 0`: return `1` (base case).
  - If `n > 0`: recursively calculate `n * factorial (n - 1)`.
  - If `n < 0`: raise an error — factorial isn’t defined for negatives in this context.

- **`main` Function**:
  - Prompts the user.
  - Reads input and converts it to `Int`.
  - Calls `factorial` and prints the result.

---

