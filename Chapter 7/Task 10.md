HC17T10: Implement the Monoid instance for the Config data type, where the identity element is a configuration with the lowest loggingLevel, highest timeout, and lowest retries.
---



```haskell
-- Define the Config type
data Config = Config
    { loggingLevel :: Int
    , timeout      :: Int
    , retries      :: Int
    } deriving (Show)

-- Semigroup instance: combine using max and min logic
instance Semigroup Config where
    (<>) (Config l1 t1 r1) (Config l2 t2 r2) =
        Config
            (max l1 l2)  -- prefer higher loggingLevel
            (min t1 t2)  -- prefer shorter timeout
            (max r1 r2)  -- prefer higher retries

-- Monoid instance: define the identity Config
instance Monoid Config where
    mempty = Config
        { loggingLevel = 0        -- lowest possible level
        , timeout      = maxBound -- maximum timeout
        , retries      = 0        -- lowest retries
        }

-- Demo
main :: IO ()
main = do
    let cfg1 = Config 1 100 2
    let cfg2 = Config 3 60 1
    let merged = cfg1 <> cfg2 <> mempty
    putStrLn $ "🧩 Combined Config: " ++ show merged
```

---

### 🧠 Explanation

- **Semigroup Instance**: Uses domain-specific logic to combine fields.
- **Monoid Instance**:
  - `mempty` is the "neutral" config:
    - `loggingLevel = 0`: least verbose
    - `timeout = maxBound`: gives most time possible
    - `retries = 0`: lowest retry count

- **Why `Monoid` is Useful**:
  - Allows using `mconcat`, folds, and default configs naturally.
  - Enables elegant composition of optional or layered settings.

---

