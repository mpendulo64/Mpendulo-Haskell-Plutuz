 HC15T8: Define a function using the Either type to provide detailed error messages for division.
---



```haskell
-- Safe division with detailed error handling using Either
safeDiv :: (Eq a, Fractional a, Show a) => a -> a -> Either String a
safeDiv _ 0 = Left "Error: Division by zero is not allowed."
safeDiv x y = Right (x / y)

-- Helper function to print Either result
printResult :: (Show a) => Either String a -> IO ()
printResult (Left err)  = putStrLn err
printResult (Right val) = putStrLn $ "Result: " ++ show val

-- Main function to test safeDiv
main :: IO ()
main = do
    let x = 10
    let good = safeDiv x 2
    let bad  = safeDiv x 0

    putStrLn "Dividing 10 by 2:"
    printResult good

    putStrLn "\nDividing 10 by 0:"
    printResult bad
```

---

## 📘 Explanation

### ✅ `Either String a`

* `Either` is used for computations that may **fail with a reason**.
* Convention:

  * `Left` represents an **error** (e.g. `Left "Bad input"`)
  * `Right` represents a **successful result**

---

### ✅ Function logic

```haskell
safeDiv _ 0 = Left "Error: Division by zero is not allowed."
safeDiv x y = Right (x / y)
```

* Checks for divide-by-zero
* Returns a descriptive `Left` error on failure
* Returns `Right result` otherwise

---

