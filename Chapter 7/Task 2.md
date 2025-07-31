HC17T2: Define a Min and Max newtype for any Ord type and implement their respective Semigroup instances using min and max.
---



```haskell
-- Min wrapper for any Ord type
newtype Min a = Min { getMin :: a }
    deriving (Eq, Show)

-- Semigroup instance using min
instance Ord a => Semigroup (Min a) where
    Min x <> Min y = Min (min x y)

-- Max wrapper for any Ord type
newtype Max a = Max { getMax :: a }
    deriving (Eq, Show)

-- Semigroup instance using max
instance Ord a => Semigroup (Max a) where
    Max x <> Max y = Max (max x y)

-- Optional: Monoid instances (identity = "neutral" value)
instance (Ord a, Bounded a) => Monoid (Min a) where
    mempty = Min maxBound
    mappend = (<>)

instance (Ord a, Bounded a) => Monoid (Max a) where
    mempty = Max minBound
    mappend = (<>)

-- Example usage
main :: IO ()
main = do
    let a = Min 5
    let b = Min 3
    let c = Max 7
    let d = Max 10

    putStrLn $ "🌡️ Min 5 <> Min 3 = " ++ show (a <> b)
    putStrLn $ "🌡️ Max 7 <> Max 10 = " ++ show (c <> d)
```

---

### 🧠 Explanation

- **`newtype Min a` / `Max a`**: These wrap any `Ord` type, allowing us to create specialized instances.
- **`Semigroup instance`**: Uses `min` or `max` to combine wrapped values.
- **`Monoid instance`** (optional):
  - `Min` uses `maxBound` as identity so it doesn't affect comparison.
  - `Max` uses `minBound` as identity for the same reason.
- **Why `newtype`?**: It's efficient and type-safe. It avoids ambiguity when combining values semantically.

---



