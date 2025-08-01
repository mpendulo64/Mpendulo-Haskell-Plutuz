HC18T10: Create a function nestedFmap that applies a function to a nested structure using multiple fmap calls.
---
```haskell
-- Applies a function to a value inside a nested Functor structure
nestedFmap :: (Functor f, Functor g) => (a -> b) -> f (g a) -> f (g b)
nestedFmap = fmap . fmap

-- Example usage
main :: IO ()
main = do
    let maybeList = Just [1, 2, 3]
    let ioMaybe   = return (Just 10) :: IO (Maybe Int)
    let listTuples = [("x", 1), ("y", 2)]

    putStrLn "🌀 Applying (+1) to nested structures:"
    print $ nestedFmap (+1) maybeList     -- Just [2,3,4]
    result <- nestedFmap (*2) ioMaybe     -- IO (Just 20)
    print result
    print $ nestedFmap (*3) listTuples    -- [("x",3),("y",6)]
```

---

### 🧠 Explanation

- **`nestedFmap = fmap . fmap`**:
  - First `fmap` lifts into the outer structure.
  - Second `fmap` lifts into the inner structure.
- Works for any **two-layer Functor**: `f (g a)`.
- Examples:
  - `Maybe [a]` → outer `Maybe`, inner `[]`
  - `IO (Maybe a)` → outer `IO`, inner `Maybe`
  - `[(a, b)]` → outer `[]`, inner `(,) a` (remember: tuples are Functors over the second element)

---

