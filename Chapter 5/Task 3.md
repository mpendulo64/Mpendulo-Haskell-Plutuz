HC5T3: Checking for Uppercase Letters

---

```haskell
import Data.Char (isUpper)

-- Function to check if any word starts with an uppercase letter
hasCapitalStart :: [String] -> Bool
hasCapitalStart = any startsWithCapital
  where
    startsWithCapital []     = False
    startsWithCapital (x:_)  = isUpper x
```

---

### 🧠 Explanation

- `hasCapitalStart :: [String] -> Bool`:  
  This function takes a list of strings (words) and returns `True` if any word starts with an uppercase letter, otherwise `False`.

- `any startsWithCapital`:  
  The `any` function checks if the predicate `startsWithCapital` returns `True` for at least one element in the list.

- `startsWithCapital (x:_) = isUpper x`:  
  This helper function checks if the first character of a word is uppercase using `isUpper`.

- `startsWithCapital [] = False`:  
  Handles the edge case of an empty string.

---



```haskell
*Main> hasCapitalStart ["hello", "world"]
False

*Main> hasCapitalStart ["hello", "World"]
True

*Main> hasCapitalStart ["", "apple", "Banana"]
True
```

