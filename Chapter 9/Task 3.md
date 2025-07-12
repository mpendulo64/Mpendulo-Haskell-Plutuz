HC9T3: Define a Function to Add Values in a Box

---



```haskell
-- Define the Box type
data Box a = Empty | Has a
    deriving Show

-- Define addN for Box containing numeric values
addN :: Num a => a -> Box a -> Box a
addN n Empty     = Empty
addN n (Has x)   = Has (n + x)

-- Example usage
main :: IO ()
main = do
    let emptyBox = Empty :: Box Int
    let fullBox  = Has 10
    print (addN 5 emptyBox)  -- Output: Empty
    print (addN 5 fullBox)   -- Output: Has 15
```

---

### 🧠 Explanation:

- **`addN :: Num a => a -> Box a -> Box a`**
  - The type class constraint `Num a =>` ensures that `addN` can only operate on boxes containing numeric values (e.g. `Int`, `Float`, etc.).
  - The first argument is the number to add.
  - The second argument is the box.

- **Pattern Matching**:
  - If the box is `Empty`, we return `Empty` unchanged.
  - If it’s `Has x`, we compute `Has (n + x)` — the new boxed value.

---

