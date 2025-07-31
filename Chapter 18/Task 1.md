HC18T1: Define a function mapToLower using fmap that converts all characters in a list to lowercase.
---



```haskell
import Data.Char (toLower)

-- Use fmap to convert each character to lowercase
mapToLower :: String -> String
mapToLower = fmap toLower

-- Demo usage
main :: IO ()
main = do
    let input = "HeLLo WoRLd!"
    let result = mapToLower input
    putStrLn $ "🔤 Lowercase: " ++ result
```

---

### 🧠 Explanation

- **`String`** is just `[Char]`, and lists are functors — so we can use `fmap` to apply a function to every element.
- **`toLower`** is a standard function from `Data.Char` that converts a character to its lowercase equivalent.
- **`mapToLower = fmap toLower`** is functionally identical to `map toLower`, but highlights the beauty of `Functor`.

---

