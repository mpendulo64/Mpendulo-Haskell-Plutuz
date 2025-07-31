HC17T1: Create a Severity data type representing the severity of an emergency with four levels (Low, Medium, High, Critical). Implement a Semigroup instance for this type, where the higher severity overrides the lower one.


---



```haskell
-- Define the Severity data type with increasing severity
data Severity = Low | Medium | High | Critical
    deriving (Eq, Show, Ord)

-- Semigroup instance: higher severity overrides lower one
instance Semigroup Severity where
    (<>) = max

-- Optional: make Severity a Monoid (identity is Low)
instance Monoid Severity where
    mempty = Low
    mappend = (<>)

-- Example usage
main :: IO ()
main = do
    let a = Medium
    let b = High
    let c = Low
    let d = Critical

    putStrLn $ "🚨 " ++ show a ++ " <> " ++ show b ++ " = " ++ show (a <> b)
    putStrLn $ "🚨 " ++ show c ++ " <> " ++ show a ++ " = " ++ show (c <> a)
    putStrLn $ "🚨 " ++ show b ++ " <> " ++ show d ++ " = " ++ show (b <> d)
```

---

### 🧠 Explanation

- **`Severity`**: A simple algebraic data type with four constructors. Thanks to `Ord`, they are ordered automatically by the order in which they’re declared.
- **`Semigroup instance`**:
  - Defines `(<>) = max`, meaning when combining two severities, the higher one wins.
- **`Monoid instance`** (optional):
  - Sets `Low` as the neutral identity (`mempty`), so combining with `Low` doesn’t increase severity.
- **`main`**:
  - Demonstrates how combining different severity levels selects the most severe one.

---

