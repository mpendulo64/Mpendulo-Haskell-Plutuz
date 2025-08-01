HC18T5: Define a Functor instance for the Either type, applying fmap only to the Right case.
---



```haskell
-- Define Either type manually (for illustration)
data Either a b = Left a | Right b
    deriving (Show, Eq)

-- Functor instance applies fmap only to Right
instance Functor (Either e) where
    fmap _ (Left x)  = Left x
    fmap f (Right y) = Right (f y)

-- Example usage
main :: IO ()
main = do
    let val1 = Right 10 :: Either String Int
    let val2 = Left "Error" :: Either String Int

    putStrLn "🔁 Applying fmap (*2) to Either values:"
    print $ fmap (*2) val1  -- Right 20
    print $ fmap (*2) val2  -- Left "Error"
```

---

### 🧠 Explanation

- **`Either a b`**: Represents a value that can be either `Left a` (often an error) or `Right b` (a success).
- **`Functor (Either e)`**:
  - Only applies the function to the `Right` value.
  - Leaves `Left` untouched — preserving the error or alternative.
- **Why `Functor (Either e)` instead of `Either a b`?**
  - Functor must be applied to a type constructor of kind `* -> *`, so we fix the `Left` type and map over the `Right`.

---

