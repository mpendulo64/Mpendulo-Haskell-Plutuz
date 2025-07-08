HC4T1 - Task 1: Define a weatherReport Function

```haskell
-- Function to describe the weather using pattern matching
weatherReport :: String -> String
weatherReport "sunny"  = "It's a bright and beautiful day!"
weatherReport "rainy"  = "Don't forget your umbrella!"
weatherReport "cloudy" = "A bit gloomy, but no rain yet!"
weatherReport _        = "Weather unknown"

-- Testing the function with various inputs
main :: IO ()
main = do
    putStrLn $ "sunny: " ++ weatherReport "sunny"    -- Expected: bright and beautiful
    putStrLn $ "rainy: " ++ weatherReport "rainy"    -- Expected: don't forget your umbrella
    putStrLn $ "cloudy: " ++ weatherReport "cloudy"  -- Expected: a bit gloomy
    putStrLn $ "windy: " ++ weatherReport "windy"    -- Expected: unknown
```

---

### 🧠 How it Works:

- **Pattern matching** allows you to match exact string values directly.
- Each line defines a case:
  - `"sunny"` → cheerful message ☀️
  - `"rainy"` → umbrella warning ☔
  - `"cloudy"` → a neutral note ☁️
  - `_` (underscore) is a **wildcard** for any other unmatched input—this handles unexpected or unknown weather terms.

---

### ✅ Sample Output:

```
sunny: It's a bright and beautiful day!
rainy: Don't forget your umbrella!
cloudy: A bit gloomy, but no rain yet!
windy: Weather unknown
```
