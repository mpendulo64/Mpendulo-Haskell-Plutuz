HC15T10: Create a velocity program that uses both Either and IO exceptions to demonstrate hybrid error handling.

* ✅ **`Either`**: for detailed validation errors (e.g. bad input, divide-by-zero)
* ✅ **`try`**: to catch and handle **file I/O exceptions**

---



```haskell
import System.IO
import Control.Exception
import Text.Read (readMaybe)
import Data.Typeable

-- Custom validation using Either
safeDiv :: Double -> Double -> Either String Double
safeDiv _ 0 = Left "Error: Time cannot be zero (division by zero)."
safeDiv d t = Right (d / t)

-- Safe string parsing using Either
parseDouble :: String -> Either String Double
parseDouble s =
    case readMaybe s of
        Just x  -> Right x
        Nothing -> Left $ "Invalid number format: '" ++ s ++ "'"

-- Read distance from file with IO exception handling
readDistanceFromFile :: FilePath -> IO (Either String Double)
readDistanceFromFile path = do
    result <- try (readFile path) :: IO (Either IOException String)
    case result of
        Left ioErr -> return $ Left $ "File error: " ++ show ioErr
        Right content -> return $ parseDouble (trim content)

-- Helper: remove surrounding whitespace
trim :: String -> String
trim = unwords . words

-- Main program
main :: IO ()
main = do
    putStrLn "Reading distance from file 'distance.txt'..."
    distanceResult <- readDistanceFromFile "distance.txt"

    case distanceResult of
        Left err -> putStrLn err
        Right distance -> do
            putStrLn $ "Distance: " ++ show distance ++ " meters"
            putStrLn "Enter time (in seconds):"
            timeStr <- getLine

            case parseDouble timeStr >>= safeDiv distance of
                Left err      -> putStrLn $ "Calculation error: " ++ err
                Right velocity -> putStrLn $ "Velocity = " ++ show velocity ++ " m/s"
```

---

## 📘 Explanation

| Part              | Purpose                                                             |
| ----------------- | ------------------------------------------------------------------- |
| `try`             | Catches file I/O exceptions like missing file or permission errors  |
| `Either String a` | Handles expected validation errors like bad input or divide-by-zero |
| `readMaybe`       | Safely parses string into `Double`                                  |
| `safeDiv`         | Prevents division by zero                                           |
| `trim`            | Removes extra spaces/newlines from file content                     |

---

## 🧪 Example 1: Successful Run

**File `distance.txt` contains:**

```
100
```

**User input:**

```
20
```

**Output:**

```
Distance: 100.0 meters
Velocity = 5.0 m/s
```

---

## 🧪 Example 2: File Not Found

**File missing**

**Output:**

```
File error: distance.txt: openFile: does not exist (No such file or directory)
```

---

## 🧪 Example 3: Bad User Input

**User enters:**

```
abc
```

**Output:**

```
Calculation error: Invalid number format: 'abc'
```

---

## ✅ Why Hybrid Error Handling?

* `IO` exceptions are for unpredictable runtime errors (e.g. file not found)
* `Either` is for **expected, controllable failures** (e.g. invalid input)
* Keeps your logic **pure and composable**, while still handling **real-world IO errors**

---

