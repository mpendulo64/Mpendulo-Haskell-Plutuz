HC13T7
Write a program that imports a function from your custom SumNonEmpty module and calculates the sum of a list of numbers
---

### 📦 Step 1: Create the Module File (`SumNonEmpty.hs`)

```haskell
module SumNonEmpty (sumNonEmpty) where

-- Returns the sum of a non-empty list or throws an error
sumNonEmpty :: [Int] -> Int
sumNonEmpty []     = error "❌ Cannot sum an empty list."
sumNonEmpty values = sum values
```

- **Only `sumNonEmpty` is exported**, and helper logic (like the error message) is encapsulated inside the module.

---

### 🚀 Step 2: Main Program Using the Module (`Main.hs`)

```haskell
import SumNonEmpty (sumNonEmpty)

main :: IO ()
main = do
    let numbers = [4, 8, 15, 16]
    let result = sumNonEmpty numbers
    putStrLn $ "🧮 The sum of the list is: " ++ show result
```

---

### 🧠 Explanation

- **Module Design**:
  - `SumNonEmpty.hs` defines the functionality for summing non-empty lists with built-in error handling.
  - You import it using `import SumNonEmpty (sumNonEmpty)` so that only `sumNonEmpty` is exposed.

- **In `main`**:
  - A list of integers is defined.
  - `sumNonEmpty` calculates the total.
  - `putStrLn` prints the result with a friendly format.

---

