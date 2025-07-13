HC12T2
Write a function addTwoNumbers that takes two integers as input and returns their sum. The result should be printed using the main function.
---



```haskell
-- Define the addTwoNumbers function
addTwoNumbers :: Int -> Int -> Int
addTwoNumbers x y = x + y

-- Main program to demonstrate its usage
main :: IO ()
main = do
    let a = 7
    let b = 13
    let result = addTwoNumbers a b
    putStrLn $ "🧮 The sum of " ++ show a ++ " and " ++ show b ++ " is " ++ show result
```

---

### 🧠 Explanation

- **`addTwoNumbers :: Int -> Int -> Int`**  
  Declares the function type signature — it takes two `Int` values and returns an `Int`.

- **`x + y`**  
  Performs simple addition.

- **In `main`**:  
  - `a` and `b` are example inputs (you can swap these with values from `getLine` for interactive input).  
  - `result` computes the sum.  
  - `putStrLn` prints a formatted message with the result using `show` to convert numbers to strings.

---

