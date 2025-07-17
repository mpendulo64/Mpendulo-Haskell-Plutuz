HC14T5: Write a Haskell program that uses a custom data type Result a and demonstrate pattern matching using the @ symbol.

* ✅ Defines a **custom data type** `Result a`
* ✅ Uses **pattern matching with the `@` symbol** (as-patterns)
* ✅ Demonstrates usage in a working `main` function

---



```haskell
-- Define a custom Result type
data Result a = Success a | Error String deriving (Show)

-- Function that handles Result using pattern matching with '@'
handleResult :: Result Int -> String
handleResult r@(Success val) = "Success with value " ++ show val ++ " (full: " ++ show r ++ ")"
handleResult r@(Error msg)   = "Error occurred: " ++ msg ++ " (full: " ++ show r ++ ")"

-- Main function to test the pattern matching
main :: IO ()
main = do
    let res1 = Success 42
    let res2 = Error "Something went wrong"

    putStrLn $ handleResult res1
    putStrLn $ handleResult res2
```

---

## 📘 Explanation

### ✅ Custom Data Type

```haskell
data Result a = Success a | Error String
```

* `Result` is a generic (polymorphic) type similar to `Either` or `Maybe`.
* It can represent either:

  * `Success a` — holds a result of type `a`
  * `Error String` — holds an error message

---

### ✅ As-Pattern (`@`) Usage

```haskell
handleResult r@(Success val) = ...
```

* `r@(Success val)` is an **as-pattern**.
* It lets you **name the whole value as `r`**, **while also pattern matching** on `Success val`.
* So:

  * `val` holds the inner value (e.g., `42`)
  * `r` holds the whole `Success 42`, which you can reuse or show

This is useful for logging, debugging, or referencing the original value while still deconstructing it.

---

