HC17T9: Define a Config data type with fields for loggingLevel, timeout, and retries. Implement a Semigroup instance that combines configurations by taking the maximum loggingLevel and retries and the minimum timeout.


---



```haskell
-- Define the Config data type
data Config = Config
    { loggingLevel :: Int
    , timeout      :: Int
    , retries      :: Int
    } deriving (Show)

-- Semigroup instance: combine by max loggingLevel & retries, min timeout
instance Semigroup Config where
    (<>) (Config l1 t1 r1) (Config l2 t2 r2) =
        Config
            (max l1 l2)  -- Prefer higher logging level
            (min t1 t2)  -- Prefer lower timeout
            (max r1 r2)  -- Prefer more retries

-- Example usage
main :: IO ()
main = do
    let cfg1 = Config 2 30 3
    let cfg2 = Config 4 20 5
    let combined = cfg1 <> cfg2
    putStrLn $ "🛠️ Combined Config: " ++ show combined
```

---

### 🧠 Explanation

- **`Config` Structure**:
  - `loggingLevel` and `retries` are merged by taking the maximum — assuming higher means more verbose or more tolerant.
  - `timeout` is merged by taking the minimum — shorter timeout is likely safer or more aggressive.
  
- **Why `Semigroup`?**:
  - You're defining a way to merge configs that doesn't rely on a default value like `Monoid` would.

---
