HC4T2 - Task 2: Define a dayType Function

```haskell
-- Function to determine if a day is a weekday or weekend
dayType :: String -> String
dayType day =
  case map toLower day of
    "saturday" -> "It's a weekend!"
    "sunday"   -> "It's a weekend!"
    "monday"   -> "It's a weekday."
    "tuesday"  -> "It's a weekday."
    "wednesday"-> "It's a weekday."
    "thursday" -> "It's a weekday."
    "friday"   -> "It's a weekday."
    _          -> "Invalid day"
  where
    toLower c
      | 'A' <= c && c <= 'Z' = toEnum (fromEnum c + 32)
      | otherwise            = c
```

---

### 🧠 Explanation

- `dayType :: String -> String`: This declares the type of the function — it takes a `String` (the name of the day) and returns a `String` (the message).
- `map toLower day`: Converts the input string to lowercase so that the function is case-insensitive (e.g., "Monday", "monday", or "MONDAY" all work).
- `case ... of`: Pattern matching is used to compare the lowercase version of the input against all valid days.
- `where toLower`: A helper function that converts a character to lowercase (ASCII-based). This avoids needing to import external libraries like `Data.Char`.

---
