HC14T8: Implement a function counts that returns a list of tuples showing character frequency in a string.
---


```haskell
import Data.List (group, sort)
import qualified Data.Char as Char

-- Function to count character frequencies in a string
counts :: String -> [(Char, Int)]
counts str =
    map (\grp -> (head grp, length grp)) $
    group $
    sort str

-- Main to test the function
main :: IO ()
main = do
    let input = "hello world"
    print $ counts input
```

---

## 📘 Explanation

### ✅ Goal:

Convert a string like `"hello world"` into:

```haskell
[(' ',1),('d',1),('e',1),('h',1),('l',3),('o',2),('r',1),('w',1)]
```

---

### ✅ Step-by-step breakdown

```haskell
counts str =
    map (\grp -> (head grp, length grp)) $
    group $
    sort str
```

1. `sort str` – Sorts the string so that repeated characters are adjacent:

   * `"hello"` → `"ehllo"` → `"ehllo"`
2. `group` – Groups identical adjacent characters into sublists:

   * `"ehllo"` → `["e", "h", "ll", "o"]`
3. `map (\grp -> (head grp, length grp))` – Turns each group into a `(Char, Int)` pair:

   * `["l","l","l"]` → `('l', 3)`

---



