HC19T10: Create a function combineResults that combines two Either values using applicative style.
---


```haskell
-- Combines two Either values using applicative style
combineResults :: Either String Int -> Either String Int -> Either String Int
combineResults x y = pure (+) <*> x <*> y

-- Example usage
main :: IO ()
main = do
    print $ combineResults (Right 3) (Right 5)     -- ✅ Should return Right 8
    print $ combineResults (Left "Error A") (Right 5) -- ❌ Should return Left "Error A"
    print $ combineResults (Right 3) (Left "Error B") -- ❌ Should return Left "Error B"
```

---

### 🧠 Explanation

- **`Either e a`** is an instance of `Applicative`:
  - `pure` wraps a value in `Right`.
  - `<*>` applies a function inside `Right` to another `Right` value.
  - If either value is `Left`, the computation short-circuits and returns the first `Left`.

- **`combineResults`**:
  - Uses `pure (+)` to lift the addition function.
  - Applies it to two `Either String Int` values.
  - If both are `Right`, it computes the sum.
  - If either is `Left`, it returns the error.

---

