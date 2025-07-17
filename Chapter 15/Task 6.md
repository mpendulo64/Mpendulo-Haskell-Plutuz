HC15T6: Use readMaybe to parse user input safely and avoid runtime errors during input parsing.
---


```haskell
import Text.Read (readMaybe)

-- Function to safely read a number and respond
getNumberFromUser :: IO ()
getNumberFromUser = do
    putStrLn "Enter a number:"
    input <- getLine
    case readMaybe input :: Maybe Int of
        Just n  -> putStrLn $ "You entered the number: " ++ show n
        Nothing -> putStrLn "Invalid input! Please enter a valid integer."

-- Main function
main :: IO ()
main = do
    getNumberFromUser
```

---

## 📘 Explanation

### ✅ `readMaybe :: Read a => String -> Maybe a`

* Tries to parse a string into a value of type `a`
* Returns `Just a` on success
* Returns `Nothing` on failure — instead of crashing like `read`

---

### ✅ What happens

#### Input:

```
42
```

#### Output:

```
You entered the number: 42
```

#### Input:

```
hello
```

#### Output:

```
Invalid input! Please enter a valid integer.
```

---

### ✅ Why use `readMaybe`?

* `read` is **unsafe** — crashes on bad input:

  ```haskell
  read "abc" :: Int  -- runtime error!
  ```

* `readMaybe` is **safe** — returns `Nothing` instead:

  ```haskell
  readMaybe "abc" :: Maybe Int  -- Nothing
  ```

---

