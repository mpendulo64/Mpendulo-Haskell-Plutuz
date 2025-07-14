HC13T5
Refactor the sumNonEmpty function to restrict the visibility of helper functions like error messages in the module export list.


---



```haskell
module SumNonEmpty (sumNonEmpty) where

-- Internal error message (not exported)
errorMessage :: String
errorMessage = "❌ Cannot compute sum of an empty list."

-- Core sum function that hides internals
sumNonEmpty :: [Int] -> Int
sumNonEmpty []     = error errorMessage
sumNonEmpty values = sum values
```

---

### 🧠 Explanation

- **`module SumNonEmpty (sumNonEmpty)`**:  
  Only exports `sumNonEmpty` — the public interface.

- **Helper `errorMessage`** is **not listed in the export list**, so it’s private to this module.

- If other modules import `SumNonEmpty`, they can’t access `errorMessage`, keeping implementation clean and encapsulated.

- This design aligns with **information hiding** and **module boundaries**, helping you write maintainable Haskell libraries.

---

