HC11T7: Implement the Ord instance for the Box type using the compare function
To do this, we’ll make a few design decisions:

- An `Empty` box will be considered less than a `Has` box.
- Two `Has` boxes will be compared by their contents.
- This requires that the contained type `a` already be an instance of `Ord`.

---



```haskell
-- Define the Box type
data Box a = Empty | Has a
    deriving (Show, Eq)

-- Implement Ord for Box using compare
instance Ord a => Ord (Box a) where
    compare Empty Empty       = EQ
    compare Empty (Has _)     = LT
    compare (Has _) Empty     = GT
    compare (Has x) (Has y)   = compare x y

-- Example usage
main :: IO ()
main = do
    let box1 = Empty :: Box Int
    let box2 = Has 42
    let box3 = Has 100

    print $ compare box1 box2  -- LT
    print $ compare box2 box1  -- GT
    print $ compare box2 box3  -- LT
    print $ compare box2 box2  -- EQ
```

---

### 🧠 Explanation

- **Pattern Matching on Box**:
  - `Empty` compared to `Empty` returns `EQ`.
  - `Empty < Has _`, so returns `LT`.
  - `Has _ > Empty`, so returns `GT`.
  - `Has x` vs `Has y`: compares values directly using `compare x y`.

- **`Ord a => Ord (Box a)`**:
  - Ensures this only works when the boxed type `a` can be compared with `Ord`.

- **Flexible & Consistent Ordering**:
  - You can now sort or use `Box` in ordered data structures (`Set`, `Map`, etc.) if the underlying type supports it.

---

