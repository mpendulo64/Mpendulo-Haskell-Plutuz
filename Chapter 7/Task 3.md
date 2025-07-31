HC17T3: Implement the Monoid instance for the Severity type, where the identity value is Low.


---



```haskell
-- Define the Severity type with ordered constructors
data Severity = Low | Medium | High | Critical
    deriving (Eq, Show, Ord)

-- Semigroup instance: higher severity overrides lower one
instance Semigroup Severity where
    (<>) = max

-- Monoid instance: identity element is Low
instance Monoid Severity where
    mempty = Low
    mappend = (<>)

-- Example usage
main :: IO ()
main = do
    let a = Medium
    let b = Critical
    let c = Low

    putStrLn $ "🔥 Medium <> Critical = " ++ show (a <> b)
    putStrLn $ "🔥 mempty <> Medium = " ++ show (mempty <> a)
    putStrLn $ "🔥 Low <> Low = " ++ show (c <> c)
```

---

### 🧠 Explanation

- **Semigroup instance**:
  - Uses `max`, so when two severity levels are combined, the more urgent one wins.
- **Monoid instance**:
  - `mempty` is `Low`, meaning it doesn't raise severity if combined.
  - This makes `Severity` suitable for folding over lists with `mconcat`.

---

