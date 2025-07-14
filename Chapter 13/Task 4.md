HC13T4
Write a Haskell module named SumNonEmpty that defines a function sumNonEmpty, which returns an error if called on an empty list.


---


```haskell
module SumNonEmpty (sumNonEmpty) where

-- Sum function that errors on empty input
sumNonEmpty :: [Int] -> Int
sumNonEmpty []     = error "❌ Cannot compute sum of an empty list."
sumNonEmpty values = sum values
```

---

### 🧠 Explanation

- **`module SumNonEmpty (sumNonEmpty)`**  
  Declares the module and exposes only the `sumNonEmpty` function.

- **Function Logic**:
  - If the list is empty (`[]`), it triggers an error using Haskell’s `error` function with a clear message.
  - Otherwise, it delegates to the standard `sum` function.

---

### 🚀 Usage Example (in `Main.hs`)

```haskell
import SumNonEmpty (sumNonEmpty)

main :: IO ()
main = do
    let list1 = [3, 7, 2]
    let list2 = []

    putStrLn $ "✅ Sum of list1: " ++ show (sumNonEmpty list1)

    -- Uncomment below to see the error in action
    -- putStrLn $ "Sum of list2: " ++ show (sumNonEmpty list2)
```

---

